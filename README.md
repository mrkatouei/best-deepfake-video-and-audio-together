# Deep fake: Speaker-Aware Talking-Head Animation

This is the code repository implementing the paper:

> **Deep fake: Speaker-Aware Talking-Head Animation**
>
> [Yang Zhou](https://people.umass.edu/~yangzhou), 
> [Xintong Han](http://users.umiacs.umd.edu/~xintong/), 
> [Eli Shechtman](https://research.adobe.com/person/eli-shechtman), 
> [Jose Echevarria](http://www.jiechevarria.com) , 
> [Evangelos Kalogerakis](https://people.cs.umass.edu/~kalo/), 
> [Dingzeyu Li](https://dingzeyu.li)
>
> SIGGRAPH Asia 2020
>
> **Abstract** We present a method that generates expressive talking-head videos from a single facial image with audio as the only input. In contrast to previous attempts to learn direct mappings from audio to raw pixels for creating talking faces, our method first disentangles the content and speaker information in the input audio signal. The audio content robustly controls the motion of lips and nearby facial regions, while the speaker information determines the specifics of facial expressions and the rest of the talking-head dynamics. Another key component of our method is the prediction of facial landmarks reflecting the speaker-aware dynamics. Based on this intermediate representation, our method works with many portrait images in a single unified framework, including artistic paintings, sketches, 2D cartoon characters,  Japanese mangas, and stylized caricatures.
In addition, our method generalizes well for faces and characters that were not observed during training. We present extensive quantitative and qualitative evaluation of our method, in addition to user studies, demonstrating generated talking-heads of significantly higher quality compared to prior state-of-the-art methods.
>
> [[Project page]](https://people.umass.edu/~yangzhou/Deep fake/) 
> [[Paper]](https://people.umass.edu/~yangzhou/Deep fake/Deep fake_SIGGRAPH_Asia_Final_round-5.pdf) 
> [[Video]](https://www.youtube.com/watch?v=OU6Ctzhpc6s) <!-- [[Arxiv]](https://arxiv.org/abs/1907.11308) -->

![img](doc/teaser.png)

Figure. Given an audio speech signal and a single portrait image   as input (left), our model generates speaker-aware talking-head animations (right). 
Both the speech signal and the input face image are not observed during the model training process.
Our method creates both non-photorealistic cartoon animations (top) and natural human face videos (bottom).

## Requirements
- Python environment 3.6
```
conda create -n deep fake_env python=3.6
conda activate deep fake
```
- ffmpeg (https://ffmpeg.org/download.html)
```
sudo apt-get install ffmpeg
```
- python packages
```
pip install -r requirements.txt
```

## Pre-trained Models (to release soon)

Download the following pre-trained models to `examples/ckpt` folder.

| Model |  Link to the model | 
| :-------------: | :---------------: |
| Voice Conversion  | [Link](https://)  |
| Speech Content Module  | [Link](https://)  |
| Speaker-aware Module  | [Link](https://)  |
| Image2Image Translation Module  | [Link](https://)  |
| Non-photorealistic Warping (.exe)  | [Link](https://)  |

## Animate You Portraits!

`Nature human faces / Paintings` (warping through Image-to-image translation module)

- crop your portrait image into size `256x256` and put it under `examples` folder with `.jpg` format. 
Make sure the head is almost in the middle (check existing examples for a reference).

- put test audio files under `examples` folder as well with `.wav` format.

- animate!

```
python main_end2end.py --jpg <portrait_file>  
```

- use addition args `--amp_lip_x <x> --amp_lip_y <y> --amp_pos <pos>` 
to amply lip motion (in x/y-axis direction) and head motion displacements, default values are `<x>=2., <y>=2., <pos>=1.`



`Non-photorealistic cartoon faces` (warping through Delaunay triangulation)

- animate one of the existing puppets

| Puppet Name |  wilk | roy | sketch | color | cartoonM | danbooru1 | 
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Image  | ![img](examples_cartoon/wilk_fullbody.jpg)  | ![img](examples_cartoon/roy_full.png)  | ![img](examples_cartoon/sketch.png)  | ![img](examples_cartoon/color.jpg)  | ![img](examples_cartoon/cartoonM.png)  | ![img](examples_cartoon/danbooru1.jpg)  |

```
python main_end2end_cartoon.py --jpg <cartoon_puppet_name>
```

- create your own puppets (ToDo...)

## Train

ToDo...

## [License](LICENSE.md)


