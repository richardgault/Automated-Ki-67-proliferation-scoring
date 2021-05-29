# Automated-Ki-67-proliferation-scoring

This repository contains the relevant files to implement the modelling work outlined in: McConnell et. al. XXXX. This work was developed by Miranda McConnell and has utilised a number of open-source libraries

## Background

The Ki-67 protein is associated with cell proliferation and is a clinical marker for breast cancer tumour aggressiveness. The percentage of immunopositive cells present in a histological image stained for Ki-67 expression informs the proliferation index quantifying tumour aggressiveness. This deep learning based model automatically detects cells, identifies whether they are Ki-67 immunopositive or immunonegative and calculate the Ki-67 proliferation scores for stained histological images.

## Pre-requisites

This model was developed using dataset outlined in:  
```
Negahbani, F., Sabzi, R., Pakniyat Jahromi, B. et al. PathoNet introduced as a deep neural network backend for evaluation of Ki-67 and tumor-infiltrating lymphocytes in breast cancer. Sci Rep 11, 8489 (2021). https://doi.org/10.1038/s41598-021-86912-w
```

We would like to thank them for sharing their dataset and encourage you to visit their webpage http://shiraz-hidc.com for information of how to contact the authors and visit their repository: https://github.com/SHIDCenter/PathoNet.

Other datasets can be used with the code included in this repository provided the following guidelines are followed:

* Mask Generation ():
* The following file structure was used during the development of this work and it is recommended an analogous structure is used when running the code from this repository
  * All Data
    * training data raw images (png)
    * training data labels (JSON)
    * training ground truth masks (generated using: ) (png)
    * validation data raw images (png)
    * validation data labels (JSON)
    * validation ground truth masks (generated using: )(png)
    * test data raw images (png) 
    * test data labels (JSON)
    * test data ground truth masks (generated using: )(png)
* Annotated labels in JSON files.  

All code can be run using Google Colab for easy access to GPU resources. Check that GPU is utilised in Colab by going to Edit -> Notebook Settings -- and ensure hardware accelerator is set to GPU. Depending on the size of the data you are analysing Colab may suggest that you have ran out of memory when running the Model training. It may be possible to easily resolve this by Runtime -> Factory reset runtime. Alterating model hyperparameters (e.g. batch size) may also help but may lead to a change in model performance.

## Usage
```python
import foobar

foobar.pluralize('word') # returns 'words'
foobar.pluralize('goose') # returns 'geese'
foobar.singularize('phenomena') # returns 'phenomenon'
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT] https://github.com/richardgault/Automated-Ki-67-proliferation-scoring/blob/main/LICENSE
