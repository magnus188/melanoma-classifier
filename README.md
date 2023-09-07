# Classification of skin cancer from images of moles

## Model Descriptions:

### Model 1: Basic Model
**Structure**: 
- Normalization layer
- Three convolutional blocks each with:
  - Conv2D layer with 32 filters of size 3x3 and ReLU activation
  - MaxPooling2D layer
- Flatten layer
- Dense layer with 128 units and ReLU activation
- Dense layer with a number of units equal to `num_classes`.
  
**Characteristics**:
- A simple convolutional neural network (CNN) designed as a baseline for image classification tasks.
- Uses ReLU as the activation function which is widely used due to its computational efficiency.
- The final dense layer determines class probabilities.

### Model 2: Base + Data Augmentation
**Structure**: 
- Data Augmentation layer
- [All layers from the Basic Model]

**Characteristics**: 
- Builds upon the Basic Model by introducing a data augmentation layer at the beginning.
- Data augmentation helps artificially increase the size of the training dataset by applying random, realistic modifications to the training images, aiding in improving model generalization.
- Common augmentations include random rotations, zooms, shifts, and flips.

### Model 3: Base + Data Augmentation + Additional Layers
**Structure**: 
- [All layers from Model 2]
- Conv2D layer with 32 filters of size 3x3 without activation
- LeakyReLU activation layer
- Conv2D layer with 32 filters of size 3x3 without activation
- BatchNormalization layer
- LeakyReLU activation layer
- Conv2D layer with 64 filters of size 5x5 with ReLU activation
- GlobalAveragePooling2D layer

**Characteristics**: 
- This model further builds upon Model 2 by introducing more convolutional layers and a global average pooling layer.
- The LeakyReLU activation function is introduced, which allows a small gradient when the unit is not active, potentially helping with the vanishing gradient problem in deep networks.
- Batch normalization is added to improve the training speed, reduce the dependency on the initialization, and act as a form of regularization, potentially preventing overfitting.
