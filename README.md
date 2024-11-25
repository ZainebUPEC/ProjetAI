# Glasses Detection Model with Mask R-CNN
This project aims to develop a glasses detection model using Mask R-CNN. We collect images, label them, convert the annotations into COCO format, and create mask images for training.

# Project Workflow
1. Dataset Selection and Labeling
Dataset Collection: We collected a dataset of images where glasses are visible, to train a glasses detection model.
Labeling with Labelbox: We uploaded these images to Labelbox, a platform for image annotation. We used Labelbox to annotate each image, marking the regions where glasses are present using polygon annotations.
<img width="1440" alt="Screenshot 2024-11-11 at 16 51 28" src="https://github.com/user-attachments/assets/d282a6b6-33e2-4b95-a458-f29b36e5028e">

3. Exporting masks from Labelbox
Once the annotations were complete, we exported them from Labelbox

4. Conversion Script: We wrote a Python script that reads images and annotation details, and converts them into the COCO JSON format. This format is compatible with Mask R-CNN and includes:

images: Metadata for each image (ID, filename, width, height).
annotations: Polygon segmentation data for glasses regions.
categories: Single category for "glasses."
Output: The output file, follows the COCO format structure and is ready for use in model training.
