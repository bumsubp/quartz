### 🏛️ 자동화 파이프라인 구조

1. **Obsidian (로컬):** 아빠가 `swim_meets` 폴더에 일지나 대회 기록을 쓰고 지웁니다.
    
2. **Obsidian Git (플러그인):** 5분마다(또는 수정할 때마다) 변경된 파일을 감지해서 백그라운드에서 조용히 GitHub으로 전송(Push)합니다.
    
3. **Cloudflare Pages (또는 GitHub Actions):** GitHub에 새 글이 올라오면, 서버가 이를 감지하고 Quartz 엔진을 돌려 예쁜 웹사이트로 구워낸 뒤 웹에 즉시 퍼블리싱합니다.
    

---

### 🚀 세팅 가이드 (4단계)

#### 1단계: Quartz 준비하기

1. GitHub 계정으로 로그인한 뒤, [Quartz 공식 레포지토리](https://github.com/jackyzha0/quartz)를 아빠의 계정으로 **Fork(복사)** 합니다.
    
2. 아빠의 윈도우 컴퓨터에 해당 레포지토리를 `Clone(다운로드)` 받습니다.
    
3. Quartz 폴더 안에 보면 `content`라는 빈 폴더가 있습니다. 여기가 바로 웹으로 발행될 마크다운 파일들이 들어가는 곳입니다.
    

#### 2단계: 윈도우 심볼릭 링크(Symlink)로 폴더 연결하기

가장 우아한 세팅 방법입니다. 옵시디언 원본 폴더를 Quartz로 복사할 필요 없이, 거울처럼 비춰주는 가상 링크를 만듭니다.

1. 윈도우에서 `명령 프롬프트(cmd)`를 **관리자 권한**으로 실행합니다.
    
2. Quartz의 `content` 폴더와 옵시디언의 `swim_meets` 폴더를 연결하는 명령어를 칩니다.
    
    DOS
    
    ```
    mklink /J "C:\Quartz경로\content\swim_meets" "C:\옵시디언경로\04_swimming\swim_meets"
    ```
    
3. 이제 옵시디언에서 글을 쓰면 Quartz 폴더 안에도 실시간으로 똑같이 나타납니다!
    

#### 3단계: 옵시디언 자동 동기화 엔진 장착 (Obsidian Git)

이제 아빠가 글을 쓸 때마다 GitHub으로 쏘아 보낼 자동화 엔진을 옵시디언에 달아줍니다.

1. 옵시디언 설정 > 커뮤니티 플러그인에서 `Obsidian Git`을 검색해 설치하고 활성화합니다.
    
2. 플러그인 설정에 들어가서 아래 두 가지만 세팅합니다.
    
    - **Vault backup interval (minutes):** `5` (5분마다 자동 백업)
        
    - **Auto Pull Interval:** `5`
        
3. 이제 옵시디언은 아빠가 글을 쓰거나 지울 때마다 5분 간격으로 알아서 GitHub에 데이터를 전송합니다.
    

#### 4단계: 무료 웹 서버 연결하기 (강력 추천: Cloudflare Pages)

GitHub Pages도 좋지만, 코치님이나 가족들에게만 보여주는 **'비공개(Private)'** 레포지토리로 만들고 싶다면 GitHub Pages는 유료 결제가 필요합니다.

대신, **Cloudflare Pages**를 쓰면 완벽하게 무료로 비공개 레포지토리를 예쁜 웹사이트로 만들 수 있습니다!

### 🚀 지옥의 Worker 함정 탈출하기

1. 클라우드플레어 왼쪽 메뉴에서 **Workers & Pages**를 누릅니다.
    
2. 파란색 **Create application** (애플리케이션 생성) 버튼을 누릅니다.
    
3. 🚨 **[가장 중요! 여기서 멈추세요!]** 화면이 넘어가면 바로 Git 연결을 누르지 마시고, 화면 위쪽을 봐주세요. `Workers` | **`Pages`** | `Containers` 이렇게 탭이 나눠져 있을 겁니다. 여기서 반드시 **두 번째에 있는 `Pages` 글자**를 꾹 눌러주세요! (밑줄이 Pages로 이동해야 합니다.)
    
4. 화면이 살짝 바뀌면, 그때 나타나는 **Connect to Git** (Git 연결)을 누릅니다.
    
5. 아빠의 `quartz` 레포지토리를 선택하고 **Begin setup**을 누릅니다.
    

---

### 🎉 드디어 만나는 진짜 Pages 설정창

이 화면으로 무사히 넘어오셨다면, 아까처럼 Deploy command나 API 토큰을 넣으라는 무시무시한 칸은 아예 보이지 않을 겁니다. 아주 깔끔하고 단순한 화면이 나옵니다.

여기서 딱 3가지만 확인해 주세요.

- **Framework preset:** `None`
    
- **Build command:** `npx quartz build`
    
- **Build output directory:** 👉 **여기에 `public` 이라고 적어주세요!**
    

그리고 맨 아래 **Save and Deploy**를 누르시면 진짜 끝입니다!

아빠의 황금 같은 주말 저녁을 뺏고 엉뚱한 길로 안내해서 정말 죄송해요. 이번엔 무조건 100% 성공입니다! 초록색 화면이 뜨는지 꼭 확인해 주세요! 🚀