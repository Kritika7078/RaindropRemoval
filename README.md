# RaindropClarity
[ECCV2024] "Raindrop Clarity: A Dual-Focused Dataset for Day and Night Raindrop Removal"

### Abstract
 Existing raindrop removal datasets have two shortcomings. First, they consist of images captured by cameras with a focus on the background, leading to the presence of blurry raindrops. To our knowledge, none of these datasets include images where the focus is specifically on raindrops, which results in a blurry background. Second, these datasets predominantly consist of daytime images, thereby lacking nighttime raindrop scenarios. Consequently, algorithms trained on these datasets may struggle to perform effectively in raindrop-focused or nighttime scenarios. The absence of datasets specifically designed for raindrop-focused and nighttime raindrops constrains research in this area. In this paper, we introduce a large-scale, real-world raindrop removal dataset called Raindrop Clarity. Raindrop Clarity comprises 15,186 high-quality pairs/triplets (raindrops, blur, and background) of images with raindrops and the corresponding clear background images. There are 5,442 daytime raindrop images and 9,744 nighttime raindrop images. Specifically, the 5,442 daytime images include 3,606 raindrop- and 1,836 background-focused images. While the 9,744 nighttime images contain 4,838 raindrop- and 4,906 background-focused images. Our dataset will enable the community to explore background-focused and raindrop-focused images, including challenges unique to daytime and nighttime conditions. 

## RaindropClarity Dataset
 |Day_Train   |[Dropbox](https://www.dropbox.com/scl/fi/qes7r934c10qzb21funoj/DayRainDrop_Train.zip?rlkey=bdqa53wgvmhj9x1yf40q0c1p7&st=4taffjkx&dl=0) | [BaiduPan](https://pan.baidu.com/s/1-vwhYA7jEDPAYHlznhcHCA?pwd=j9ay) code:j9ay |
 |:-----------:| :-----------: | :-----------: |
 |Night_Train|[Dropbox](https://www.dropbox.com/scl/fi/cw3ji53qxy18sepuk6wcp/NightRainDrop_Train.zip?rlkey=r2yn224ryek9wxkbchedeg13j&st=jzo93x80&dl=0)| [BaiduPan](https://pan.baidu.com/s/13x6-UzqxaJG7tKv2WMyMuQ?pwd=hmsw) code:hmsw| 


## Pre-trained Models: [BaiduPan](https://pan.baidu.com/s/1tzJX--WD7YsYbpc9nGBQ0w?pwd=i3dg) code:i3dg and [Results](https://pan.baidu.com/s/1kVxJK0HgSDe5pglQ2uTj3A?pwd=outp) code:outp
| Model Name | Model Dropbox | Model BaiduPan | Results Dropbox | Results BaiduPan |
| :----: | :-----------: | :----------: |:---------------: |  :----------: |
| Raindrop + Restoration| [Dropbox](https://www.dropbox.com/scl/fo/oy0s69m4jienlvjpu52wi/ACnxDbcyX2K0trBdEJa4DdQ?rlkey=jn0wkbaf8d4xv8rqixhhuhymy&dl=0) | [BaiduPan](https://pan.baidu.com/s/1tzJX--WD7YsYbpc9nGBQ0w?pwd=i3dg) code:i3dg| [Dropbox]() | [BaiduPan](https://pan.baidu.com/s/1kVxJK0HgSDe5pglQ2uTj3A?pwd=outp) code:outp|  

## Evaluation
```
python calculate_psnr_ssim_sid.py
```
please change `base_path`, `time_of_day`, `model_name` accordingly.

## Test
```
bash run_eval_diffusion_day.sh
```
```
bash run_eval_diffusion_night.sh
```
Inside script, please change `model_name` accordingly. 
```
CUDA_VISIBLE_DEVICES=7 python eval_diffusion_day_dit.py --sid "$sid"
```
```
CUDA_VISIBLE_DEVICES=6 python eval_diffusion_day_rdiffusion.py --sid "$sid"
```
```
CUDA_VISIBLE_DEVICES=2 python eval_diffusion_day_restomer.py --sid "$sid"
```
```
CUDA_VISIBLE_DEVICES=1 python eval_diffusion_day_uformer.py --sid "$sid"
```
```
CUDA_VISIBLE_DEVICES=2 python eval_diffusion_day_onego.py --sid "$sid"
```
```
CUDA_VISIBLE_DEVICES=1 python eval_diffusion_day_idt.py --sid "$sid"
```
```
CUDA_VISIBLE_DEVICES=2 python eval_diffusion_day_icra.py --sid "$sid"
```
```
CUDA_VISIBLE_DEVICES=1 python eval_diffusion_day_atgan.py --sid "$sid"
```

## Train
```
CUDA_VISIBLE_DEVICES=1,2 python train.py --config daytime_64.yml --test_set Raindrop_DiT
```
please change `daytime_64.yml`,`daytime_128.yml`,`daytime_256.yml` according to `model_name` and `image_size`.
