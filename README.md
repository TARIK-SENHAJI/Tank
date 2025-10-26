The process includes:

Environment Setup: Installing necessary libraries like Roboflow, Supervision, FlashAttention, and the YOLOv12 model directly from its GitHub repository.

GPU Check: Verifying the availability of a compatible NVIDIA GPU, noting that FlashAttention requires an Ampere architecture or newer.

Data Acquisition: Downloading a custom "classavehicle" dataset from Roboflow in YOLOv12 format.

Data Preparation: Modifying the dataset's data.yaml file to ensure the path configurations are correct for training.

Model Training: Fine-tuning a yolov12s model on the custom data for 100 epochs.

Evaluation: Assessing the trained model's performance by displaying confusion matrices, results charts, and calculating Mean Average Precision (mAP) metrics (mAP 50:95, mAP 50, mAP 75) using the test set.

Inference: Loading the best-trained weights (best.pt) and running predictions on random images from the test set, then visualizing the detected bounding boxes and labels.
