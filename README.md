# Codebase associated with paper: "Before And After Pseudoscience: An Empirical Challenge to Social Classification using Facial Recognition"

## Abstract

A number of researchers and companies claim to be able to discern social category membership (criminality, sexual orientation, political orientation, etc.) using facial recognition tools, and suggest on that basis that these categories have a biological basis that can be detected with automated tools. Possible use cases suggested include policing applications, and government surveillance. Critics have raised ethical, political and methodological challenges to these claims. Here we conduct an empirical investigation of a study that claims to be able to discern political orientation from images of faces posted to social media, with the aim of teasing out how much of the predictive power of the model can be attributed to grooming and presentation choices rather than deeper biological characteristics. We create a novel dataset consisting of pairs of images of where one individual is presenting themselves differently in the two images. These pairs of images are drawn from searches for “before and after” images from makeovers, haircuts, and drag. We re-implement the political orientation detection model and use it to classify the images from our dataset, to determine test-retest reliability. Individuals' predicted political orientations differ for the two images 33% of the time. We also retrain the models to predict “before” and “after” categories on the new dataset, and achieve prediction accuracy of 68%, which is comparable to the political orientation model's results. These findings suggest that superficial presentation differences, not biological factors, are responsible for comparable categorization results.

## Requirements

To install requirements, run:

```bash
pip install -r requirements.txt
```

## Dataset

Datasets can from logistic regression and neural network models are the same as the original paper being re-implemented [\[1\]](#ref) and can be downloaded from this link. [https://osf.io/c58d3/](https://osf.io/c58d3/)

Download the `RData` files to `/data/original` and run:

```python
python ./data/convert_rdata_to_numpy.py
```
This outputs a `vgg.npy` containing the features and `faces.csv` containing the labels. This data can be loaded at any time using the functions provided in `data/load_data.py`.

Unfortunately the dataset for "Before and After" dataset cannot be made public to preserve anonymity and privacy of persons pictured. Unfortunately this limits the reproducibility of the project. We have however made public the exact scripts used to scrape the images (available [here](https://anonymous.4open.science/r/bing-search-image-scraping-EFB1)) and the search terms used to generate images detailed in the paper. We also made available a tool for labelling images more efficiently [here](https://anonymous.4open.science/r/tkinter-image-labeller-gui-01F3/).

Please note that the experiments were run in Jupyter Lab environment.

## Models

To train the models run the notebooks `notebooks/train_lasso_regression.ipynb` and `notebooks/train_neural_net.ipynb` to train the logistic regression model and neural network respectively. `train_lasso_regression_cross_validation.ipynb` is also available as a means to reproduce Table 2 of the original paper.

## Tests

Running test-retest will unfortunately require the before after dataset which cannot be made public for privacy concerns. Steps to reproduce the dataset however are provided in the paper. If you have the dataset regenerated and can proceed with test-retest analysis, please ensure that the pre-trained weights for ResNet-50 model using VGGFace2 dataset are available. While the original weights provided by the authors of VGGFace2 are no longer available, a backup of it can be found [here](https://queensuca-my.sharepoint.com/:u:/g/personal/21rfk_queensu_ca/EQ7o1aRxfIFNprDBi0H01sQBp7rmAKfyu-Jwjk3K3AHJWA?e=gAPoQs). Download it and copy the weights as `saved_model/resnet50_ft_weight.pkl`.



## Reference

<span id="ref">[\[1\] M. Kosinski, “Facial recognition technology can expose political orientation from naturalistic facial images,” Scientific Reports, vol. 11, no. 1, Art. no. 1, Jan. 2021, doi: 10.1038/s41598-020-79310-1.](https://www.nature.com/articles/s41598-020-79310-1)</span>


