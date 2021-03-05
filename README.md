# neural-style-transfer

Neural Style Transfer (NST) refers as a class of software algorithm manipulate digital images, or videos, or adopt the appearance or visual style of another image. When we implement the algorithm, we define two distances; one for the content (Dc) and another for the form (Ds).

In the topic, we will implement an artificial system based on Deep Neural Network, which will create images of high perceptual quality. The system will use neural representation to separate, recombine content-image (a style image) as input, and returns the content image as it is printed using the artistic style of the style image.

Neural style transfer is an optimization technique mainly used to take two images- a content image and a style reference image and blend them. So, the output image looks like the content image to match the content statistics of the content image and style statistics of the style reference image. These statistics are derived from the images using a convolutional network.

![1](https://github.com/rjnp2/neural-style-transfer/blob/master/images/style-transferring.png)

## Working of the neural style transfer algorithm
When we implement the given algorithm, we define two distances; one for the style (Ds) and the other for the content (Dc). Dc measures the different the content is between two images, and Ds measures the different the style is between two images. We get the third image as an input and transform it into both minimize its content-distance with content-image and its style-distance with the style-image.

- **VGG-19 model** \
  VGG-19 model is similar to the VGG-16 model. Simonyan and Zisserman introduced the VGG model. VGG-19 is trained on more than a million images from ImageNet database. This model has 19 layers of the deep neural network, which can classify the images into 1000 object categories.
  
  ![1](https://github.com/rjnp2/neural-style-transfer/blob/master/images/style-transferring2.png)

- **High-level architecture** \
  Neural style transfer uses a pertained convolution neural network. Then define a loss function which blends two images absolutely to create visually appealing art, NST defines the following inputs:

  - A content image (c)- Image we want to transfer a style to
  - A styling image (s)- The image we want to move the method from
  - An input image (g) - The image which contains the final result.
  
  The architecture of the model is same, as well as the loss, which is computed, is shown below. We do not need to develop a profound understanding of what is going on in the image below, as we will see each component in detail in the next several sections to come. The idea is to give a high-level of understanding of the workflow taking place style transfer.
  
  ![1](https://github.com/rjnp2/neural-style-transfer/blob/master/images/style-transferring3.png)

- **Loss functions** \
  In the section, we define two loss functions; the style loss function and the content function. The content loss function ensures that the activation of the higher layer is similar between the generated image and the content image.

  - **Content cost function** \
      The content cost function is sure that the content present in the content image is captured into the generated image. It has been found that CNN captures information about the content in the higher levels, where the lower levels are more focused on single-pixel values.

      Let A^l_{ij}(I) is the activation of the lth layer, ith feature map, and j th position achieve using the image I. Then the content loss is defined as
      
      ![1](https://github.com/rjnp2/neural-style-transfer/blob/master/images/style-transferring4.png)

      If we visualize what is learned by a neural network, there's evidence that suggests that different features maps in higher layers are activated in the presence of various objects. So if two images have the same content, they have similar activations in the top tiers.
  
  - **Style Loss function** \
      It define the style loss function which desires more work. To derive the style information from the VGG network, we will use full layers of CNN. Style information is measured the amount of correlation present between feature maps in a layer. Mathematically, the style loss is defined as,
      
      ![1](https://github.com/rjnp2/neural-style-transfer/blob/master/images/style-transferring5.png)

      **Intuition behind the style loss**
      By the above equation system the idea is simple. The main goal is to compute a style matrix for the originated image and the style image.

      Then, the style loss is defined as a root mean square difference between the two styles matrices.
      
      ![1](https://github.com/rjnp2/neural-style-transfer/blob/master/images/style-transferring6.png)

