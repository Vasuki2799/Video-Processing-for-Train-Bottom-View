# Video Processing for Train Bottom View

## Author
**Vasuki A**  
[LinkedIn](https://www.linkedin.com/in/vasuki27/)  
Email: vasukiarul27@gmail.com

---

## Project Objective
The goal of this project is to develop a video processing system to analyze train videos, specifically from side/bottom views, to:  
1. Split a full train video into smaller segments of each coach.  
2. Count the number of coaches.  
3. Detect major items: door, door open, door close.  
4. Generate a structured report summarizing the counts and representative frames.

---

## Project Workflow

### 1. Data Collection
- Input: 5 videos capturing trains from side/bottom views.  
- Some videos contained identifiable train numbers, some were unknown/random.  
- Videos included slow-moving trains for better frame extraction.

### 2. Frame Extraction
- Used OpenCV to extract frames from each video at regular intervals.  
- Saved extracted frames into folders organized by train number.

### 3. Model Training
- Developed a Convolutional Neural Network (CNN) for classification:
  - Classes: `door`, `door_open`, `door_close`, `background`  
  - Image size: 128×128  
  - Data augmentation: rotation, width/height shift, shear, zoom, horizontal flip  
- Trained the model on extracted frames from videos.

### 4. Prediction & Annotation
- Loaded the trained CNN model (`train_model.h5`)  
- Annotated frames with predicted labels using OpenCV.  
- Created annotated videos (`.avi`) showing predictions on each frame.

### 5. Count Coaches and Doors
- Processed annotated frames to compute:
  - Total coaches (assuming 1 door per coach)  
  - Number of doors, door open, door close  
- Generated representative frames for each coach.

### 6. PDF Report Generation
- Compiled counts and representative frames into a PDF report.  
- Included a table summarizing each train’s stats:
  - Total coaches  
  - Doors, door open, door close  
- Embedded sample frames to visualize detection results.

---

## Challenges Faced
- **Partial visibility:** Some videos showed only train wheels; doors were not visible → counts were 0.  
- **Limited data:** Few videos were available, requiring careful handling of train number assignments.  
- **Model accuracy:** CNN validation accuracy was low for some classes due to limited annotated frames.  
- **Framework constraints:** OpenCV display issues on Google Colab required saving annotated videos instead of real-time display.

---

## Observations & Conclusion
- The system successfully detects and counts coaches with visible doors.  
- Videos where doors were not visible showed 0 counts — expected behavior.  
- The generated PDF report provides a clear overview of train composition and door states.  
- This pipeline demonstrates how video processing and CNN-based object detection can analyze complex sequences efficiently.

---

## Tools & Libraries
- Python 3.x  
- OpenCV  
- TensorFlow / Keras  
- NumPy  
- FPDF (for PDF report)  
- Google Colab (for execution)

---

## File Structure
Train_Coach_Detection/
├── data/                   # Sample frames (optional)

├── model/

│   └── train_model.h5      # Trained CNN model

├── scripts/

│   ├── frame_extraction.py

│   ├── train_cnn.py

│   ├── annotate_frames.py

│   └── count_coaches.py

├── videos/

│   ├── output.avi

│   ├── output1.avi

│   └── ...

├── report.pdf              # Generated PDF report




