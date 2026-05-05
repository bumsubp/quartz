## 🏊‍♀️ [[Swimming]] 

- **Training Type**: `INPUT[inlineListSuggester(optionQuery("04_swimming/training_type")):swimming_training_type]`

- **Main Strokes**: `INPUT[inlineListSuggester(optionQuery("04_swimming/strokes")):swimming_main_strokes]` 
 
- **Practice Time (min)**: `INPUT[number:swimming_minutes]`

- **Routine:** `INPUT[textArea:swimming_routine]`
- **Dryland Training**: `INPUT[inlineListSuggester(optionQuery("04_swimming/dryland_training")):swimming_dryland_training]`
- `INPUT[inlineListSuggester(optionQuery("04_swimming/dryland_training")):category]`

`INPUT[inlineListSuggester("04_swimming/dryland_training/01_Upper_Body_and_Injury_Prevention", "04_swimming/dryland_training/02_Back_and_Stroke_Power", "04_swimming/dryland_training/03_Lower_Body_and_Start"):category]`

- **Note**:`INPUT[textArea:swimming_note]`

## 🎹 [[Piano]] 

- **Current Repertoire**: `INPUT[inlineListSuggester(optionQuery("03_piano/piano_pieces")):piano_piece]` 

- **Practice Time (min)**: `INPUT[number:piano_minutes]`

- **Note**:`INPUT[textArea:piano_note]`
# 📚 [[English]]

- **Books**: `INPUT[inlineListSuggester(optionQuery('"02_academics/English/english_books" and #book')):english_books]` 

- **Units**: `INPUT[text:english_unit]`

- **Status:** `INPUT[suggester(option("🔄 In-Progress"), option("✅ Done")):english_status]`

- **Note**:`INPUT[textArea:english_note]`

# 🔢 [[Math]]

- **Books**:  `INPUT[inlineListSuggester(optionQuery('"02_academics/Math/math_books" and #book')):math_books]` 

- **Units**: `INPUT[text:math_unit]`

- **Status:** `INPUT[suggester(option("🔄 In-Progress"), option("✅ Done")):math_status]`

- **Note**:`INPUT[textArea:math_note]`
# 💡 Today's Comments

- **Comment**: `INPUT[textArea:daily_comments]`