![waving](https://capsule-render.vercel.app/api?type=waving&height=200&text=SkinDeep&fontAlign=80&fontAlignY=40&color=gradient)

# [SkinDeep](https://github.com/vijishmadhavan/SkinDeep) &nbsp; [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?text=Skin%20Deep&url=https://github.com/vijishmadhavan/SkinDeep&via=Vijish68859437&hashtags=machinelearning,developers,100DaysOfCode,Deeplearning) &nbsp;

__Contact__: vijishmadhavan@gmail.com

I planned this project after watching Justin Bieber's "Anyone" Music Video, He had his tattoo covered up with the help of artists airbrushing on him for hours. The results were amazing in the music video. Producing that sought of video output can be difficult, so I opted for Images. Can deep learning do a decent job or can it even match photoshop? This was the starting point of this project!!

## Why not photoshop?

Photoshop can produce extremely good results but it needs expertise and hours of work retouching the whole image.

### Allen Iverson's(American basketball player) tattoo removed using this model.

![Imgur](https://i.imgur.com/mEuf6CX.gif)

## Highlights

- [Example Outputs](#Example-Outputs) &#x1F537;
- [Getting Started Yourself](#Getting-Started-Yourself) &#x1F537;


# Synthetic data generation

To do such a project we need a lot of image pairs, I couldn't find any such dataset so I opted for synthetic data.

(1) Overlaying APDrawing dataset image pairs along with some background removed tattoo designs, This can be easily done using Python OpenCV.

(2) Apdrawing dataset has line art pairs which will mimic tattoo lines, this will help the model to learn and remove those lines.

(3) APDrawing dataset only has portrait head shots, For full body images I ran my previous ArtLine(https://github.com/vijishmadhavan/ArtLine) project and overlaid the output with the input image.

![Imgur](https://i.imgur.com/RYSBhcg.jpg)


![Imgur](https://i.imgur.com/sm66zlt.jpg)

(4) ImageDraw.Draw was used with forest green colour codes and placed randomly on zoomed-in body images, Similar to Crappify in fast.ai.

(5) Photoshop was also used to place tattoos in subjects where warping and angle change was needed.

![Imgur](https://i.imgur.com/EcpIIGT.jpg)

Mail me for a modified Apdrawing dataset.


# Example Outputs


![Imgur](https://i.imgur.com/ALw5of3.png)


![Imgur](https://i.imgur.com/cjY7f3P.png)


![Imgur](https://i.imgur.com/A9ziYQK.png)

### Heavily tattooed faces

![Imgur](https://i.imgur.com/BrWJTp7.jpg)

![Imgur](https://i.imgur.com/VC0vJAU.jpg)

# Visual Comparison

![Imgur](https://i.imgur.com/Jytk9Qe.png)


## Technical Details

The highlight of the project is in producing synthetic data, thanks to **pyimagesearch.com** for wonderful blogs. Check below links.

https://www.pyimagesearch.com/2016/03/07/transparent-overlays-with-opencv/

https://www.pyimagesearch.com/2016/04/25/watermarking-images-with-opencv-and-python/

https://www.pyimagesearch.com/2015/01/26/multi-scale-template-matching-using-python-opencv/

* **Self-Attention** (https://arxiv.org/abs/1805.08318). Generator is pretrained UNET with spectral normalization and self-attention. Something that I got from Jason Antic's DeOldify(https://github.com/jantic/DeOldify), this made a huge difference, all of a sudden I started getting proper details around the facial features.

* **Progressive Resizing** (https://arxiv.org/abs/1710.10196),(https://arxiv.org/pdf/1707.02921.pdf). Progressive resizing takes this idea of gradually increasing the image size, In this project the image size was gradually increased and learning rates were adjusted. Thanks to fast.ai for introducing me to Progressive resizing, this helps the model to generalise better as it sees many more different images.

* **Generator Loss** :  Perceptual Loss/Feature Loss based on VGG16. (https://arxiv.org/pdf/1603.08155.pdf).

## Required libraries

This project is built around the wonderful Fast.AI library.

- **fastai==1.0.61** (and its dependencies).  Please don't install the higher versions
- **PyTorch 1.6.0** Please don't install the higher versions

## Getting Started Yourself

The project is still a work in progress, but I want to put it out so that I get some good suggestions.

The easiest way to get started is to simply try out on Colab: [<img src="https://colab.research.google.com/assets/colab-badge.svg" align="center">](https://colab.research.google.com/github/vijishmadhavan/SkinDeep/blob/master/SkinDeep_good.ipynb)

[<img src="https://colab.research.google.com/assets/colab-badge.svg" align="center">](https://colab.research.google.com/github/vijishmadhavan/SkinDeep/blob/master/SkinDeep.ipynb)

The output is limited to 500px and it needs high quality images to do well.

I would request you to have a look at the limitations given below.

## Limitations

- Synthetic data does not match real tattoos, so the model struggles a bit with some images.
- Building a huge dataset by myself was impossible, so I had to go with a limited number of image pairs.
- Tattoo designs are unique, it differs from person to person so the model might fall in some cases.
- Coloured tattoos won't work, the dataset had none.

## Going Forward

The model still struggles and needs a lot of improvement, if you are interested please contribute lets improve it.

## Acknowledgments

- Thanks to fast.ai, Jason Antic(https://github.com/jantic) and pyimagesearch.com.
