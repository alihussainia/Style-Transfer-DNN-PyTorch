# Style-Transfer-DNN-PyTorch
In this notebook, we’ll recreate a style transfer method that is outlined in the paper, <a href="https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf">Image Style Transfer Using Convolutional Neural Networks, by Gatys</a> in PyTorch.

In this paper, style transfer uses the features found in the 19-layer VGG Network, which is comprised of a series of convolutional and pooling layers, and a few fully-connected layers. In the image below, the convolutional layers are named by stack and their order in the stack. Conv_1_1 is the first convolutional layer that an image is passed through, in the first stack. Conv_2_1 is the first convolutional layer in the second stack. The deepest convolutional layer in the network is conv_5_4.

<img src='notebook_ims/vgg19_convlayers.png'/>

## Separating Style and Content
Style transfer relies on separating the content and style of an image. Given one content image and one style image, we aim to create a new, target image which should contain our desired content and style components:

- objects and their arrangement are similar to that of the `content image`
- style, colors, and textures are similar to that of the `style image`

An example is shown below, where the content image is of a cat, and the style image is of <a href="https://en.wikipedia.org/wiki/The_Great_Wave_off_Kanagawa">Hokusai's Great Wave</a>. The generated target image still contains the cat but is stylized with the waves, blue and beige colors, and block print textures of the style image!

<img src="notebook_ims/style_tx_cat.png" />

In this project, we'll use a pre-trained VGG19 Net to extract content or style features from a passed in image. We'll then formalize the idea of content and style losses and use those to iteratively update our target image until we get a result that we want. You are encouraged to use a style and content image of your own and share your work on Twitter with @udacity; we'd love to see what you come up with!
