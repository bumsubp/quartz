# 🚨 [매뉴얼] USA Swimming API 토큰 만료 시 갱신 가이드

n8n 파이프라인에서 수영 기록을 가져올 때 에러(예: `401 Unauthorized` 또는 `403 Forbidden`)가 발생한다면, 접속 권한(Token)이 만료된 것입니다. 아래 순서대로 1분 만에 새 토큰을 발급받아 교체하세요.

### 🕵️‍♂️ 1단계: 크롬 개발자 도구 열기

1. 크롬 브라우저를 열고 USA Swimming 기록 페이지에 접속합니다. 👉 [https://data.usaswimming.org/datahub/usas/individualsearch/times](https://data.usaswimming.org/datahub/usas/individualsearch/times)
    
2. 키보드에서 `F12`를 눌러 '개발자 도구'를 엽니다.
    
3. 상단 탭에서 `Network (네트워크)`를 클릭합니다.
    
4. 바로 아래 필터(Filter) 메뉴에서 `Fetch/XHR`을 클릭합니다. (잡다한 이미지나 파일들을 걸러줍니다.)
    
5. 기록을 깔끔하게 보기 위해 네트워크 창 왼쪽 위의 **🚫(Clear/지우기)** 버튼을 한 번 눌러줍니다.
    

### 🎯 2단계: 데이터 요청 발생시키고 찾기

1. 웹페이지 화면에서 소정이의 **Times(기록)** 탭을 누르거나 새로고침을 해서, 경기 기록이 화면에 나타나게 합니다.
    
2. 개발자 도구(Network 탭) 목록에 무언가 주르륵 생성됩니다.
    
3. 이름(Name) 열에서 **`jaql?trc=...`** 로 시작하는 항목을 클릭합니다.
    
4. 오른쪽 화면에 뜨는 **`Preview (미리보기)`** 탭을 눌러서, 소정이의 경기 기록 숫자들이 잘 들어있는지(진짜 데이터가 맞는지) 눈으로 확인합니다.
    

### 🪄 3단계: cURL로 통째로 복사하기

1. 찾아낸 그 **`jaql`** 항목에 마우스 **오른쪽 클릭**을 합니다.
    
2. **`Copy (복사)`** → **`Copy as cURL (bash)`** 또는 `Copy as cURL (cmd)`를 클릭합니다. _(이제 아빠의 마우스에는 새로운 URL, 인증 토큰, 페이로드 데이터가 통째로 복사되어 있습니다.)_
    

### 🔄 4단계: n8n에서 '토큰(Authorization)'만 갈아 끼우기

> **💡 핵심 팁:** 매번 전체 코드를 바꿀 필요 없습니다. 소정이의 고유번호(PersonKey)가 들어있는 Body 양식은 변하지 않으므로, 유효기간이 끝난 **'입장권(토큰)'**만 새것으로 바꿔주면 됩니다!

1. 메모장(또는 옵시디언 빈 페이지)을 열고 방금 복사한 cURL 내용을 붙여넣기 합니다.
    
2. 내용 중에서 아래와 같이 시작하는 **엄청나게 긴 암호문**을 찾습니다.
    
    - `-H "authorization: Bearer eyJhbGciOiJIUzI1NiIsI... (중략) ..."`
        
3. **`Bearer`** 부터 시작해서 따옴표(`"`)가 닫히기 전까지의 글자를 복사합니다.
    
4. **n8n으로 이동**하여 첫 번째 노드인 **`HTTP Request`** 노드를 엽니다.
    
5. 설정 중 **`Send Headers`** 부분에 있는 `Authorization`의 Value(값) 칸을 싹 지우고, 방금 복사한 새로운 토큰을 붙여넣기 합니다.
    

### 🚀 5단계: 테스트 및 저장

1. n8n 노드의 **Execute step** 버튼을 눌러 데이터가 정상적으로 다시 쏟아져 나오는지 확인합니다.
    
2. 성공했다면 파이프라인 전체를 저장(Save)합니다! 끝!
    

---

**📝 (참고용 기록) 소정이의 불변 데이터** 만약 API 주소 체계나 Body 구조 자체가 바뀌어 전체 세팅을 다시 해야 할 경우를 대비해 핵심 키워드를 남겨둡니다.

- **API URL:** `https://usaswimming.sisense.com/api/datasources/USA%20Swimming%20Times%20Elasticube/jaql`
    
- **소정이 PersonKey:** `3887876` (filter에 들어가는 equals 값)