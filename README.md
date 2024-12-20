# iitbhu_road_segmentation
Developed a road segmentation model tailored for IIT BHU roads using a custom dataset of 1,500+ images. Leveraged Roboflow for augmentation, creating 10,000+ samples. Trained U-Net &amp; DeepLabV3 models, achieving high accuracy in diverse conditions. Applications include autonomous navigation and traffic management.

The code  performs road segmentation using deep learning on labeled image data. Here’s a concise breakdown of its components and functionality:
	1.	Setup and Libraries:
	•	Required libraries like torch, fastseg, and albumentations are installed and imported for segmentation tasks, image transformations, and model architecture.
	2.	Data Preparation:
	•	Input image and mask files are processed and organized into two directories (jpeg_images for images and png_masks for segmentation masks).
	•	Images are paired with their respective masks, renamed, and resized to 512x512 for consistency.
	3.	Model Architecture:
	•	A pre-trained MobileV3Large segmentation model is loaded and fine-tuned by adding a custom head (model.last) to adapt it for binary segmentation tasks.
	4.	Dataset and Augmentation:
	•	A custom PyTorch Dataset class (Dataset_Builder) is created to handle image-mask loading and apply augmentations like rotations, Gaussian blur, and normalization using albumentations.
	5.	Training and Validation Split:
	•	The dataset is split into training (90%) and validation (10%) sets using PyTorch utilities. Dataloaders are created for batch processing during training and evaluation.
	6.	Visualization:
	•	Images and their corresponding masks are visualized to ensure the correctness of the dataset before training.
	7.	Training Loop:
	•	The model is trained for 20 epochs using AdamW optimizer and binary cross-entropy loss with logits.
	•	Progress bars (tqdm) are used for better visualization of training and validation progress.
	•	Training losses are tracked and logged for each batch and epoch.
	8.	IoU Metric:
	•	Intersection over Union (IoU) is computed to evaluate the segmentation performance quantitatively.
	9.	Validation:
	•	After training, the model’s performance is validated by calculating batch-level loss and IoU.

Key Features:
	•	Handles data augmentation and preprocessing seamlessly.
	•	Optimized for GPU training (device = 'cuda').
	•	Implements fine-tuning by unfreezing specific layers of the pre-trained model.
