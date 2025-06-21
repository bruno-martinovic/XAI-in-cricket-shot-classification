# XAI-in-cricket-shot-classification

In this repository I provide the code used in the final version of my Research Project.

The code consists of 7 Jupyter Notebooks. Each notebook has more details inside of it about how to run it.
For the notebooks requiring videos, you can provide your own or use the dataset from:
[1] Ahmad, Waqas & Munsif, Muhammad & Ullah, Habib & Ullah, Mohib & Alsuwailem, Alhanouf & Saudagar, Abdul & Muhammad, Khan & Sajjad, Muhammad. (2023). Optimized deep learning-based cricket activity focused network and medium scale benchmark. AEJ - Alexandria Engineering Journal. 73. 771-779. 10.1016/j.aej.2023.04.062.

### Video_Processing Notebook
This notebook can be used to process cricket shot videos, detailed instructions can be found in the notebook itself.
The pipeline of this notebook is:
1. Input videos in a folder with subfolders for each cricket shot type (e.g. dataset/shot_type_1/video)
2. Videos can be but are not automatically trimmed by 0.5 seconds in the beginning and 1 second at the end, this was specifically made for the dataset I used.
3. On each frame of the videos YOLOv8 is run to detect the batter and crop the video so that it shows only him. The description of how this is done is given in the code.
4. The cropped frames are then given to MediaPipe which extracts the x,y,z keypoints and saves them in a csv.

### CNN_LSTM_GradCAM
This notebook takes 10 frames from each video given to it, again in the folder with subfolders format, trains a CNN and implements Grad-CAM on it.
The pipeline of this notebook is:
1. Input videos in a folder with subfolders for each cricket shot type (e.g. dataset/shot_type_1/video)
2. Define CNN-LSTM and train it on the videos.
3. Run Grad-CAM on any instance.

### All SHOT TYPE _RF_XAI
These notebooks implement Feature Importance, Permutation Importance, SHAP, Grouped-SHAP, LIME and ALE Plots on MediaPipe + Random Forest. For each shot type the Random Forest is implemented on binary classification due to it performing better than multi-class.
The pipeline of this notebook is:
1. Convert keypoint dataset to binary.
2. Train random forest with 80-20 split.
3. Implement XAI methods on it.

### Multi-Class RF Feature Importance + SHAP
This notebook implements Feature Importance and SHAP on random-forest multiclass classification.
The pipeline of this notebook is:
1. Train random forest on multiclass classification.
2. Implement Feature Importance and SHAP.
