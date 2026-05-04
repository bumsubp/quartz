```dataview
TABLE 
    event_name AS "Event Name", 
    piece AS "Piece"
FROM #performance OR "Piano Stage"
WHERE type = "performance" AND date < date(today)
SORT date DESC
```


