# High-Level Computer Vision: CNN Implementation and Fine-Tuning Pre-trained Image-Net Pre-trained Model for Image Classification

## Requirements

For experiment logging and configuration tracking in Weights & Biases, please install the library:
`pip install wandb` in addition to the other libraries pre-imported in the assignment.



## Notes

1. Q1.C, **VisualFilter(model)** function is modified to accept an additional _boolean_ argument: before.
   When _before_ = False, the visualized filters are saved with a different filename.  
   The functional call in line at the bottom of ``ex3_convnet.py`` is changed to add this addition argument.  
2. Q2.A, To activate **BatchNormalization**, specify True/False on the command line:  
   ``python ex3_convnet.py -n True``
   ``nn.BatchNorm2d`` applied _only_ to each of the 5 convolution layers.  
   The parameter for ``nn.BatchNorm2d`` is the out_channel parameter of the previous ``nn.conv2d`` layer, i.e. 
   the value of ``h_size``.
   
3. Q3.A, To specify how many transform methods to add to compose function for data augmentation, specify int
values between [0,4]; 0 deselects all methods.

4. Q3.B, To specify dropout value: type a value between [0.1,0.9] on the command line:  
   ``python ex3_convnet.py -d 0.5``
   
5. For keeping track of the various experiments and hyperparameter configurations, we logged the evaluation metrics and
standard outputs in Weights & Biases (W & B), which can be examined [here](https://wandb.ai/pokarats/HLCV_CNN_3).
   
   
## Configure Command Line Arguments for Experiments

To configure hyperparameter values for Q1-3 experiments, specify options below

```
usage: ex3_convnet.py [-h] [-e EPOCH] [-n NORM] [-d DROPOUT] [-j JITTER]
[-a AUGMENT] [-v DISP] [-s E_STOP] [-c COMMENT]

ex3 convnet param options

optional arguments:
-h, --help            show this help message and exit

-e EPOCH, --epoch EPOCH Number of epochs [default = 20]
-n NORM, --norm NORM  Turn on Batch Normalization [True/False]
-d DROPOUT, --dropout DROPOUT Specify dropout p-value .e.g values between [0.1,0.9]
-j JITTER, --jitter JITTER Specify ColorJitter param [default = 0.2]
-a AUGMENT, --augment AUGMENT How many data augmentation techniques to add to
compose e.g. values between [1-4], 4 uses all transform techniques
-v DISP, --disp DISP  Show plots to display [default = False; plots are saved without display]
-s E_STOP, --e_stop E_STOP Apply early stop [default = False]
-c COMMENT, --comment Run comment for wandb run name [default = "q1_3"]
```
   
For Q4, see options below:

```
usage: ex3_pretrained.py [-h] [-e EPOCH] [-s E_STOP] [-f FINE_TUNE]
                         [-p LOAD_PRETRAINED] [-c COMMENT]

ex3 convnet param options

optional arguments:
  -h, --help            show this help message and exit
  -e EPOCH, --epoch EPOCH Number of epochs [default = 30]
  -s E_STOP, --e_stop E_STOP Apply early stop [default = True]
  -f FINE_TUNE, --fine_tune FINE_TUNE Fine-tune ONLY [default = True], False to update all parameters
  -p LOAD_PRETRAINED, --load_pretrained LOAD_PRETRAINED Load pre-trained weight [default = True]
  -c COMMENT, --comment COMMENT Run comment [default = 'q4a']

```
