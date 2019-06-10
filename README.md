# GAN Metrics

This repository provides the code for [An empirical study on evaluation metrics of generative adversarial networks](https://arxiv.org/abs/1806.07755).

Requirement
------

- Python 3.6.4
- torch 0.4.0
- torchvision 0.2.1
- pot 0.4.0
- tqdm 4.19.6
- numpy, scipy, math

Usage
------

- We create a demo for DCGAN training as well as computing all the metrics after each epoch.     
In the demo, final metrics scores of all epoches will be scored in `<outf>/score_tr_ep.npy`    
- If you want to compute metrics of your own images, you have to modify the codes of function `compute_score_raw()` in `metric.py` by yourself :)

```
python3 demo_dcgan.py \
--dataset cifar10 \
--cuda \
--dataroot <data_folder> \
--outf <output_folder> \
--sampleSize 2000
'''
run original dcgan:
'''
python3 dcgan_eval.py \
--dataset cifar10 \
--dataroot input_data \
--cuda \
--batchSize 16 \
--niter 200 \
--outf output_dcgan \
--sampleSize 1000
'''

run dcgan with gd:

'''
python3 demo_dcgan.py \
--dataset cifar10 \
--dataroot input_data \
--cuda \
--batchSize 16 \
--niter 200 \
--outf output_dcgan_gd \
--sampleSize 1000
'''

run model:
($model_name$=dcgan,dcgan_octconv_gd,dcgan_octconv_g)
'''
python3 gan_eval.py \
--dataset cifar10 \
--dataroot input_data \
--cuda \
--batchSize 16 \
--niter 200 \
--inputmodel $model_name$ \
--outf output_$model_name$ \
--sampleSize 1000
'''

python3 gan_eval.py \
--dataset cifar10 \
--dataroot input_data \
--cuda \
--batchSize 16 \
--niter 200 \
--inputmodel dcgan_octconv_g \
--outf output_dcgan_octconv_g \
--sampleSize 1000
