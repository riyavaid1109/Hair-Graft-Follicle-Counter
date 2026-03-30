# Hair-Graft-Follicle-Counter

### Computer Vision Pipeline for Follicular Unit Detection

### Problem Statement
Given high-resolution DSLR images of extracted hair grafts placed in a Petri dish, the goal is to:

Detect each **graft (follicular unit)**
- Count the number of **hair follicles (shafts) per graft**
- Classify grafts into:
  - 1-FU
  - 2-FU
  - 3-FU
  - 4-FU

---

### Key Concepts

- **Graft (Follicular Unit)** - White tissue blob  
- **Follicle** → Hair shaft emerging from the graft  
- Each graft contains **1-4 follicles**

---

### Approach

#### Stage 1: Petri Dish Detection
- Uses **Hough Circle Transform**
- Masks out irrelevant background
- Focuses on region of interest

#### Stage 2: Graft Detection (Blob Detection)
- Detects white tissue regions
- Techniques used:
  - Thresholding
  - Morphological operations
  - Contour filtering
- Each blob = one graft

#### Stage 3: Follicle Detection
- Extract local region per graft
- Detect hair shafts using:
  - Edge detection
  - Hough Line Transform
- Count number of shafts

#### Stage 4: Classification
- 1 shaft → 1-FU  
- 2 shafts → 2-FU  
- 3 shafts → 3-FU  
- 4 shafts → 4-FU  

---

### Challenges & Observations

- Global thresholding → failed due to background noise  
- Global Hough lines → detected fabric patterns  
- Black-hat transform → couldn't separate noise  

Final solution: **Localized processing per graft**

---

## Output

### Example

| Graft# | CX  | CY  | Area (px²) | Follicles | Class |
|--------|-----|-----|------------|-----------|--------|
| 1      | 120 | 340 | 560        | 2         | 2-FU   |
| 2      | 220 | 410 | 610        | 3         | 3-FU   |

### Tech Stack

- Python  
- OpenCV  
- NumPy  
- Matplotlib  

---

### Project Structure

├── AssignmentNotebook.ipynb  
├── images/  
├── outputs/  
└── README.md  

---
