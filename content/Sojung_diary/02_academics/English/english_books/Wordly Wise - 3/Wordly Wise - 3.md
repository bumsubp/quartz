#book
# 📖 Wordly Wise Dashboard

> [!summary] **Book Info**
> - **Total Units**: 15
> - **Objectives**: Watch 15-minute YouTube video for each unit

## 📊 Status by Unit (Automatically Updated)

```dataview
TABLE 
    choice(contains(rows.english_status, "Done"), "✅ Done", "🔄 In-Progress") AS "Status",
    max(rows.file.link) AS "Date"
FROM "diary"
WHERE contains(english_books, "Wordly Wise - 3") AND english_unit != null
GROUP BY english_unit AS "Unit"
SORT Unit ASC
```

```dataview
TABLE 
    choice(any(filter(rows, (r) => r.english_unit = "Unit 01" AND r.english_status = "Done")), "✅", "⬜️") AS "U1",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 02" AND r.english_status = "Done")), "✅", "⬜️") AS "U2",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 03" AND r.english_status = "Done")), "✅", "⬜️") AS "U3",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 04" AND r.english_status = "Done")), "✅", "⬜️") AS "U4",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 05" AND r.english_status = "Done")), "✅", "⬜️") AS "U5",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 06" AND r.english_status = "Done")), "✅", "⬜️") AS "U6",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 07" AND r.english_status = "Done")), "✅", "⬜️") AS "U7",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 08" AND r.english_status = "Done")), "✅", "⬜️") AS "U8",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 09" AND r.english_status = "Done")), "✅", "⬜️") AS "U9",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 10" AND r.english_status = "Done")), "✅", "⬜️") AS "U10",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 11" AND r.english_status = "Done")), "✅", "⬜️") AS "U11",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 12" AND r.english_status = "Done")), "✅", "⬜️") AS "U12",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 13" AND r.english_status = "Done")), "✅", "⬜️") AS "U13",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 14" AND r.english_status = "Done")), "✅", "⬜️") AS "U14",
    choice(any(filter(rows, (r) => r.english_unit = "Unit 15" AND r.english_status = "Done")), "✅", "⬜️") AS "U15"
FROM "diary"
WHERE contains(english_books, "Wordly Wise - 3")
GROUP BY english_books AS "Course"
```

```dataview
TABLE 
    english_unit AS "유닛",
    english_status AS "상태",
    english_note AS "메모"
FROM "diary"
WHERE contains(english_books, "Wordly Wise - 3") AND english_unit != null
SORT file.name DESC
```
