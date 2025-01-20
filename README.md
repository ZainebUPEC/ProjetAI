# Glasses Detection Model with Mask R-CNN
This project aims to develop a glasses detection model using `Mask R-CNN`. We collect images, label them, convert the annotations into `COCO` format, and create mask images for training.

# Project Workflow
## Data Preparation
1. **Dataset Selection and Labeling**  
   - **Dataset Collection**: We collected a dataset of images where glasses are visible, to train a glasses detection model.  
   - **Labeling with `Labelbox`**: We uploaded these images to Labelbox, a platform for image annotation. We used Labelbox to annotate each image, marking the regions where glasses are present using polygon annotations.  
   <img width="1440" alt="Screenshot 2024-11-11 at 16 51 28" src="https://github.com/user-attachments/assets/d282a6b6-33e2-4b95-a458-f29b36e5028e">  

2. **Exporting Masks from `Labelbox`**  
   Once the annotations were complete, we exported them from Labelbox.  

3. **Using Conversion Script inside `dataset_converter.ipynb`**  
   A Python script that reads images and annotation details exported using `Labelbox`, and converts them into the `COCO` JSON format. This format is compatible with `Mask R-CNN` and includes:
   - **images**: Metadata for each image (ID, filename, width, height).
   - **annotations**: Polygon segmentation data for glasses regions.
   - **categories**: Single category for "glasses."
   - **Output**: The output file follows the COCO format structure and is ready for use in model training.

## Training
The training process for the Mask R-CNN glasses detection model is outlined in the `train.ipynb` notebook. Below are the key steps:  

1. **Setup Environment**  
   - Ensure the required dependencies for Mask R-CNN (e.g., TensorFlow, Keras, and `matterport/mrcnn` library) are installed.  

2. **Load Dataset**  
   - The dataset prepared in COCO format is loaded, containing the images, annotations, and the "glasses" category.  

3. **Model Configuration**  
   - Custom configuration is defined by extending the `Config` class from Mask R-CNN. The configuration includes:
     - Number of epochs.
     - Batch size.
     - Learning rate.
     - Backbone architecture (e.g., ResNet-50 or ResNet-101).  

4. **Training**  
   - The model is trained using the COCO dataset loader. During training:
     - **Data Augmentation**: Techniques like flipping and scaling are applied to improve generalization.
     - **Checkpointing**: Model weights are saved at specified intervals to allow for recovery or further fine-tuning.
     - Training metrics like loss and accuracy are logged for monitoring.  

5. **Evaluation**  
   - The trained model is evaluated on a validation dataset to measure its performance using metrics such as:
     - Intersection over Union (IoU).
     - Precision and recall for detected regions.  

6. **Saving the Model**  
   - The final trained model weights are saved for future use in inference or further fine-tuning.  

## Collaborators
We thank the following contributors for their efforts in making this project successful:  
- **[Zaineb ABIDI]**.  
- **[Hadjer Messaoudene]**.  
