# classifying-chest-MNIST
Using the MNIST dataset to experiment with CNN and PyTorch

- [About MNIST](https://github.com/MedMNIST/MedMNIST)

## About:
#### **Purpose** Make a pipeline to predict the 14 classes from the x-rays of the chest MNIST dataset
<hr>

### Dataset: https://medmnist.com/

#### About Chest MNIST Dataset:
* ChestMNIST is an educational dataset with images of chest X-rays with labels identifying if each of these images have one of 14 classes. There are about 112000 images in the dataset. 70% for training, 10% for validation, and 20% for testing

<hr>

### <ins>**Process & Model:**</ins>

##### **Processing Data**
* Split data into the training/validation/testing sets, along with their labels
* Convert data from grayscale images (originally at 28x28 pixels) into RGB images (3x28x28 pixels) by adding another dimension (RGB) to the image

##### **Pipeline and Training**
* Used the resnet18 model (pre-trained CNN model with 18 layers), and requires RGB images as input
* Model trained for 100 epochs using GPU
* Has 2 passes (forward and backwards); Forward propagation shows the model how wrong it was and back propagation tells the model how to learn from the training data and correct itself
* Runtime of training took ~7 hours --> Progress bars used to demonstrate progress
* Tracked training and validation losses across epochs using MatPlotLib

##### **Metrics**
* Accuracies ranging from 86% to 99.8% across the classes (93.92% avg)
* Confusion Matrices created for each class
* High precision for all of the classes with a micro average of 0.947
* Low recall --> 0.56
* F1-Score: --> 0.54
* AUC --> 0.772

##### **Conclusions**
* The true positives and true negatives are almost evenly distributed among the matrices, resulting in high precision and low recall. Fewer positives compared to negatives. (i.e. in cardiomegaly there are only about a 100 positives compared to the 26000 negatives). The difference between negatives and positives and the high standard deviation of the positives in the data set resulted in the inability to achieve high recall.
* Large number of negatives in the dataset, creating potential bias in the model due to the imbalance of the positives and negatives. Due to the small amount of positive cases, despite the decent accuracy, the precision and recall were still very low. This emphasizes the importance of all the metrics, not just accuracy.
