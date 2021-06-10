# Automated-Ki-67-proliferation-scoring

This repository contains the relevant files to implement the modelling work outlined in: McConnell et. al. XXXX. This work was developed by Miranda McConnell and has utilised a number of open-source libraries. The paper can be cited as:
```
McConnell, M., Gault, R., Craig, S., Cutting, D., Rainer, A., James, J. "Automated Ki-67 proliferation scoring from histopathology images using Mobile and Cloud technology" UNDER REVIEW AT (2021) Irish Machine Vision and Image Processing Conference: Irish Pattern Recognition & Classification Society.
```

## Background

The Ki-67 protein is associated with cell proliferation and is a clinical marker for breast cancer tumour aggressiveness. The percentage of immunopositive cells present in a histological image stained for Ki-67 expression informs the proliferation index quantifying tumour aggressiveness. This deep learning based model automatically detects cells, identifies whether they are Ki-67 immunopositive or immunonegative and calculate the Ki-67 proliferation scores for stained histological images.

## Pre-requisites

This model was developed using dataset outlined in:  
```
Negahbani, F., Sabzi, R., Pakniyat Jahromi, B. et al. PathoNet introduced as a deep neural network backend for evaluation of Ki-67 and tumor-infiltrating lymphocytes in breast cancer. Sci Rep 11, 8489 (2021). https://doi.org/10.1038/s41598-021-86912-w
```

We would like to thank them for sharing their dataset and encourage you to visit their webpage http://shiraz-hidc.com for information of how to contact the authors and visit their repository: https://github.com/SHIDCenter/PathoNet.

Other datasets can be used with the code included in this repository provided the following guidelines are followed:
* The file "label_class_dict.csv" must be saved in the same directory as the data
* Raw image tiles: jpeg iamge sized 1228x1228 at objective lens 40x. These will ultimately be downsized to 256x256 so tiles of 256x256 at 8.35x would be equivalent.
* Mask Generation (Generate_Mask_from_JSON.ipynb): This notebook will take JSON files and create the mask (png) size 256x256 along with the downsized raw image tile at 256x256 in png format. It is assumed that the original image sise is 1228x1228. It is also assumed that the data has already been separated in to train/test/validation groups. Additionally, the number of actual Ki-67 positive cells in the JSON files along with the number of non-positive cells is saved to a CSV file for future reference.
* The following file structure was used during the development of this work and it is recommended an analogous structure is used when running the code from this repository
  * All Data
    * training data raw images: 256x256 at 8.35x effective magnification (i.e. 1228x1228 at 40x magnification) (png)
    * training data labels: The ground truth information for the cell classes are stored in a JSON file in the form	[{"x": 123, "y":456, "label_id": 1},{"x":321, "y":654, "label_id": 2}, ... ] where the x and y coordinate is "in the cell" and the label_id indicates the class - Ki67 positive cell (id = 1) or non-positive cell (id = 2). The example above would be the triplets for two different cells.(JSON)
    * training ground truth masks: (generated using: Generate_Mask_from_JSON.ipynb) 256x256 png with background as black (0,0,0), the non-positive cells coloured grey (128,128,128), and the ki67 cells coloured white (255,255,255)
    * validation data raw images: same format as training data raw images.
    * validation data labels: same format as training data labels
    * validation ground truth masks: same format as training ground truth masks (generated using: )(png)
    * test data raw images: same format as training/validation data raw images. 
    * test data labels: same format as training/validation data labels
    * test data ground truth masks: same format as training/validation ground truth masks (generated using: )(png)
    * Note: The file name of the training/validation/test images is contained within the filename of the corresponding label and mask files.
* Annotated labels in JSON files:  The triplets are parsed and used to to create a ground truth mask (as outlined above). The mask starts at 1228x1228 and is resized to 256x256 and saved as a png.
* The model takes the 256x256 png tile and uses the 256x256 mask to evaluate the model performance.
  
## Usage
All code can be run using Google Colab for easy access to GPU resources. Check that GPU is utilised in Colab by going to Edit -> Notebook Settings -- and ensure hardware accelerator is set to GPU. Depending on the size of the data you are analysing Colab may suggest that you have ran out of memory when running the Model training. It may be possible to easily resolve this by Runtime -> Factory reset runtime. Alterating model hyperparameters (e.g. batch size) may also help but may lead to a change in model performance.

* To train the model from scratch run Ki67Net_McConnell_et_al_train_test_val.ipynb (ensure that label_class_dict.csv" is saved in the same directory as the data)
* To run the trained model the saved model and model dictionary can be downloaded from: https://drive.google.com/file/d/1Lp5TKGmPb5QJARLinTcJFe0HStwcjkKj/view?usp=sharing, https://drive.google.com/file/d/1j30iby5wKdiKFQD4oVInp6fVuFP0VuQr/view?usp=sharing. Inference testing can be carried out on new images by running run-ki67Net_McConnell-el-al.ipynb


## Contributing
Pull requests are welcome. We would also welcome collaboration on this project or tangential projects - please contact richard.gault@qub.ac.uk.

## License
[MIT] https://github.com/richardgault/Automated-Ki-67-proliferation-scoring/blob/main/LICENSE
