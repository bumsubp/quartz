#book
# 📖 Math Innovations - Sizing Up Shapes Dashboard

> [!summary] **Book Info**
> - **Total Units**: 14
> - **Objectives**: Mirman Math Book in 2nd Grade

## 📊 Status by Unit (Automatically Updated)

```dataview
TABLE 
    choice(contains(rows.math_status, "Done"), "✅ Done", "🔄 In-Progress") AS "Status",
    max(rows.file.link) AS "Date"
FROM "01_daily_logs"
WHERE contains(math_books, "Math Innovations - Sizing Up Shapes") AND math_unit != null
GROUP BY math_unit AS "Unit"
SORT Unit ASC
```


```dataview
TABLE 
    math_unit AS "유닛",
    math_status AS "상태",
    math_note AS "메모"
FROM "01_daily_logs"
WHERE contains(math_books, "Math Innovations - Sizing Up Shapes") AND math_unit != null
SORT file.name DESC
```
