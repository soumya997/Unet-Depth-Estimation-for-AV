# Unet-Depth-Estimation-for-AV

The plan was to do depth estimation and use Unet varients for that. And train the pix2pix on the cityscape data. Except that other tasks were there too. But I was managed to do only two topics, 1. Depth estimation and 2. lane detection. I did a very basic job for doing the lane detection, use the manual ROI methods for getting the paths. I plan to look into lane detection and read some papers and use CNN based approach to solve the problems. As depth estimation is almost done here [did not really read any papers, only few articles], so i might get into depth estimation papers too.

# Experiment w/ depth extimation:
Seems like scratch Unet models are doing better than other models. Pretrained models did not really help, it also denotes that imagenet weights were not much helpful for depth estimations. I yet to experiment with data augmentation, and find the right augmentation for the model. I actually did not set my seed at the time of training, and because of that I got different results for Unet scratch model training. This was a major mistake.

<p align="center">
<img src="https://user-images.githubusercontent.com/54326088/162265871-e6801b9e-8b93-4eb6-91f5-a4db37bfff3f.png">
</p>

I tracked my experiment in wandb and also printed the logs in my triaing NBs, and based on the tracking from my notebook, the results were like this. I only trained these 8 types of models.

<pre>
<img width="500" src="https://user-images.githubusercontent.com/54326088/162267966-be3bb8b4-2409-44a0-89ab-fea12d672c6f.png"> <img width="500" src="https://user-images.githubusercontent.com/54326088/162268005-d1c27814-45fc-438f-a839-a12fc98ca44d.png"> 

</pre>



# Notebooks:
I have logged metric details, system resources utilizations (default), inference image in WandB. For more Inference image please go to that WandB Project.
|Model|Link|WandB|
|-----|------|----|
|Model: scratch Unet|[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/scratch-unet-1-log-mae-mse-r2-adam-bs-16-e40.ipynb)|[Link](https://wandb.ai/somusan/FYP%20Depth%20Estimation/runs/19c2yisf)|
|Model: Scratch Unet2|[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/scratchunet2-log-mae-mse-r2-adam-bs16-e40-lr-sched.ipynb)|[Link](https://wandb.ai/somusan/FYP%20Depth%20Estimation/runs/29uiot1l?workspace=user-somusan)|
|Model: AttenUnetScrtch|[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/attenunetscrtch-adam-bs16-e40-lr1-e4.ipynb)|[Link](https://wandb.ai/somusan/FYP%20Depth%20Estimation/runs/1lw6s1y5)|
|Model: UnetResNet50_imgnet|[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/unetresnet50-imgnet-adam-bs-16-e30-lr-1e-3.ipynb)|[Link](https://wandb.ai/somusan/FYP%20Depth%20Estimation/runs/32o516yv?workspace=user-somusan)|
|UnetResNext50_imgnet |[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/unetresnext50-imgnet-adam-bs-16-e40-lr-1e-3.ipynb)|[Link](https://wandb.ai/anony-moose-229468/FYP%20Depth%20Estimation/runs/32o516yv?apiKey=33f8af58b7667e3b954d7fba2512f20d7dc0e7a7)|
|UnetDensenet121_imgnet:|[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/unetdansenet121-e40-bs16-scheduler-on-fp16.ipynb)|[Link](https://wandb.ai/anony-mouse-229842/FYP%20Depth%20Estimation/runs/3dkl0xxa?apiKey=7efbb4a11601dbc6919ed687183a48ddc1bfbfb9)|
|Unet++Resnet50_imgnet: |[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/unet-resnet50-imgnet-adam-bs-16-e40-lr-1e-3.ipynb)|[Link](https://wandb.ai/anony-moose-229868/FYP%20Depth%20Estimation/runs/1nvwf4aa?apiKey=259067d9b6cec7b2aacbe2655de4b33ca2ea5657)|
|Unet++DensNet121|[NB](https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Notebooks/unet-densnet121.ipynb)|[Link](https://wandb.ai/anony-moose-230136/FYP%20Depth%20Estimation/runs/g0zmx4ut?apiKey=95ce55e8cb6b7e590241d27f364a7e6e59e16230)|

# Inference Results:
- Unet++DensNet121 model inference.
<img width="500" src="https://user-images.githubusercontent.com/54326088/164057710-d7581a81-e01c-4ac6-a9c4-0d68ad70cc39.png">

# Workflow:
|Pipeline|Model workflow|
|---|---|
|<img src="https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Media/Untitled%20Diagram.drawio%20(2).png">|<img src="https://github.com/soumya997/Unet-Depth-Estimation-for-AV/blob/main/Media/Untitled%20Diagram-Page-2.drawio%20(1).png">|


# TODOs:
- [ ] `DPT (Dense Prediction Transformers)`: SOTA on zero-shot depth estimation, outperforming MiDaS by 28% in relative performance. Trained on 1.4 million images. [`REFERENCE`](https://github.com/NielsRogge/Transformers-Tutorials/tree/master/DPT)
- [ ] `GLPN (Global-Local Path Networks):` takes SegFormer as backbone with a lightweight head on top. SOTA on famous benchmarks (KITTI and NYUv2). [`REFERENCE`](https://github.com/NielsRogge/Transformers-Tutorials/tree/master/GLPN)
- [ ] Read more papers on CNN based Lane Detection and Implement few of them. [`REFERENCE`](https://qiita.com/RanWensheng/items/c49e4bf3c55103546a30)






