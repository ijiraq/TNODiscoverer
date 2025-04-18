# TNODiscoverer
This repository provides tools to find TNOs with deep learning.

### [Workflow]  

Steps 1-3 are for training the model, and steps 4-6 are for using the model to detect TNOs.

|Step|File|Purpose|Input|Output|
|-|-|-|-|-|
|1|ImageCutter.ipynb|Extract sub-images for training|Injected.fits (image with injected moving objects), Injected.plantlist (List of injected sources)|Injected.npy|
|2|Concatenator.ipynb|Prepare dataset for training|Injected.npy (sub-images from ImageCutter)|Injeted_Source_Dataset.npy|
|3|Trainer.ipynb|Train the model|Injected_Source_Dataset.npy (dataset from Concatenator), Injected_Source_Information.npy (target information)|Model.h5 (trained CNN models)|
|-|-|-|-|-|
|4|ImageCutter.ipynb|Extract sub-images for detection|Images.fits (without artificial moving objects)|Images.npy|
|5|Predictor.ipynb|Apply trained model to detect objects|Images.npy (sub-images from ImageCutter), Target.npy (target info), Model.h5 (trained CNN models)|Detections.npy|
|6a|Link_sources_to_objects.py|Detect moving objects (linear fitting method)|Detections.npy (classification and regression output from Predictor)| Classification.npy|
|6b|CandidateFinder.ipynb|Detect moving objects (scoring method)|Classifcation.npy (classification output from Predictor), Target.npy (sub-images, target info)|Candidates.csv|

### Example Files
Due to the repository's capacity limit, only the following example files are included:  
- Only 4 FITS files out of 44 × 36 total.  
- Only 44 plant list files out of 44 × 36 total.
- Only 1 target file for the first CCD.
- Only 2 models (MobileNet classification and regression).  
- CNN-predicted values for sub-images of the first CCD.
