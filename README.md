# [Medical Segmentation Decathlon](http://medicaldecathlon.com)

## TODO:  
#### Step 1: Data Exploration
##### [Data stats](https://github.com/suryatejadev/medseg_decathlon/blob/master/notebooks/data_exploration.ipynb)

#### Step 2: Classification Model  
1. **Model:**
	- **Input**: Image of shape [batch_size=32, height=50, width=50, depth=50, channels=1]. Use [resize](http://scikit-image.org/docs/dev/api/skimage.transform.html#skimage.transform.resize).    
	- **Architecture**: Similar to Densenet. Remove last set of layers. Use 3D convs of size (5,5,5).  
	- **Output**: 7 classes, one for each task. Use Adam **(AdamW?)** and categorical cross entropy.  
	- **Validation**: 20% of train data.  

2.  **Data generator:**  
	- Add augmentations. Use Keras custom datagen.  
	- Sample randomly from all datasets for each batch. **(weighted sampling based on number of images in each dataset??)**  

#### Step 3: Segmentation Model  
1. **Model:**
	- **Input**: Image of shape [batch_size=32, height, width, depth=1, channels=2] **(fix the dims. Also, slice wise segmentation done)**. 1st channel: grayscale image, 2nd channel: conditioning image.   
	- **Conditioning image**: a constant intensity image for each class, uniform split of 255.   
	- **Architecture**: **UNet vs dilated Densenet ?**.
	- **Output**: Segmentation mask. Use Adam **(AdamW?)** and categorical cross entropy.  

2.  **Data generator:**  
	- Add augmentations. Use Keras custom datagen.  
	- Sample randomly from all datasets for each batch. **(weighted sampling based on number of images in each dataset??)**  

 