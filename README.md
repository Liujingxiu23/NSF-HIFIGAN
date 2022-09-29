# NSF-HIFIGAN
NSF by 王鑫

General
-------
This project is Pytorch re-implementation of NSF models.
For more information on NSF models, please visit 
https://nii-yamagishilab.github.io/samples-nsf/


## Folder structure

    | - DATA: folder to store data
    |
    | - cyc-noise-nsf-4: cyclic-noise hn-sinc-NSF
    |
    | - hn-nsf: harmonic-plus-noise NSF
    |
    | - hn-sinc-nsf-9: harmonic-plus-noise NSF with trainable sinc filter
    |
    | - hn-sinc-nsf-10: hn-sinc-nsf-9 with the BLSTM in condition module replaced by CNNs
    |
    | - hn-sinc-nsf-hifigan: hn-sinc-nsf 9 + hifi-gan discriminator 

Usuage
------
## choose one project
cd hn-nsf 

## setup the dependency and PYTHONPATH
source ../../../env.sh 

## run script
bash 00_demo.sh


This script will download the CMU database and pre-extracted features.
It then generates samples using a pre-trained model and the pre-extracted features.
It finally trains a new model on the data.

Pre-trained models are either included in __pre-trained or downloaded through 00_demo.sh.

This may take a few days or more. You may consider run 00_demo.sh in the background.


Notes
-----
1. Interactive tutorial:
   An interactive tutorial on NSF is in ../../tutorials/s1_demostration_hn-nsf.ipynb
   Please follow the README.md there to use that tutorial

2. To accelerate training:
   The default script uses torch.backends.cudnn.deterministic= True and
   torch.backends.cudnn.benchmark = False for reproducibility.
   https://pytorch.org/docs/stable/notes/randomness.html

   If you want to accelerate training, add options to the command line in 00_demo.sh
   
   python main.py --num-workers 10 --cudnn-deterministic-toggle --cudnn-benchmark-toggle

   This will set torch.backends.cudnn.deterministic=False
   and torch.backends.cudnn.benchmark = True

3. To set batch size > 1:
   python main.py --num-wokers 10 --batch-size N 


If you have any question, contact the author
