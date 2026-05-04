#book
# 📖 Math Innovations - Notable Numbers Dashboard

> [!summary] **Book Info**
> - **Total Units**: 13
> - **Objectives**: Mirman Math Book in 2nd Grade

## 📊 Status by Unit (Automatically Updated)

```dataview
TABLE 
    choice(contains(rows.math_status, "Done"), "✅ Done", "🔄 In-Progress") AS "Status",
    max(rows.file.link) AS "Date"
FROM "01_daily_logs"
WHERE contains(math_books, "Math Innovations - Notable Numbers") AND math_unit != null
FLATTEN split(math_unit, ", ") AS SingleUnit
GROUP BY SingleUnit AS "Unit"
SORT Unit ASC
```

