  

---
layout: post
title: "What's in the Future: Frame Prediction using cGAN"
description: ""
category: [technical]
tags: [ai , ml, cv, gan, cgan]
---
{% include JB/setup %}

##  Static Image Editing

### Each cell shows a frame generated using different optical flow for the same image.



<div align="center"><small>Static Image Editing</small></div>

<div align="center"><small>Each cell shows a frame generated using different optical flow for the same image.</small></div>

<table border="1" id="data">

<tbody>

<tr>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0001_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0002_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0003_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0004_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0005_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0006_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0007_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0008_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0009_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0010_input_pred.gif)</td>

</tr>

<tr>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0011_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0012_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0013_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0014_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0015_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0016_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0017_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0018_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0019_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0020_input_pred.gif)</td>

</tr>

<tr>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0021_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0022_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0023_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0024_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0025_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0026_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0027_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0028_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0029_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0030_input_pred.gif)</td>

</tr>

<tr>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0031_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0032_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0033_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0034_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0035_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0036_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0037_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0038_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0039_input_pred.gif)</td>

<td>![Snowboard](https://github.com/sidgan/sidgan.github.com/raw/master/images/gan/ms_coco_pred_1frame_40flow/ms_coco_pred_1frame_40flow/snowboard/gifs/0040_input_pred.gif)</td>

</tr>

</tbody>

</table>
