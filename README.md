# Streetlamp_Annotation_YOLO_Processing

This project automates the **processing of image annotations** from Label Studio for a dataset of **streetlamps**, and transforms the annotation data into a format suitable for **YOLO object detection training** and **database insertion**.

---

## 📌 Project Overview

The task consists of two main parts:

### ✅ TASK 1: Annotation Filtering & SQL Export

- Load annotation data from a JSON file exported from **Label Studio**
- Filter only annotations completed by a specific user (based on email)
- Extract relevant data:
  - `x`, `y`, `width`, `height`
  - `rectanglelabels` (e.g. `Pole`, `Lamp`)
  - image URL / filename
  - timestamp
- Save filtered data into a new JSON file
- Generate SQL `INSERT` statements to populate a table with this structure:

```sql
annotations (
    id INT,
    x FLOAT,
    y FLOAT,
    width FLOAT,
    height FLOAT,
    rectanglelabels TEXT,
    image TEXT,
    created_at TIMESTAMP
)
