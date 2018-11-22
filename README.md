Debag
Chainer implementation of 3D Unet for brain segmentaion.
Training configs are written at configs/base.yml.
Because of the limitation of GPU memory, we used patch based method.

Requirements
SimpleITK
Chainer v4
yaml
Network architecture
3D Unet architecture architecture

Usage
Training
To train 3D unet.

python train.py -h

optional arguments:
  -h, --help            show this help message and exit
  --gpu GPU, -g GPU     GPU ID (negative value indicates CPU)
  --base BASE, -B BASE  base directory path of program files
  --config_path CONFIG_PATH
                        path to config file
  --out OUT, -o OUT     Directory to output the result
  --model MODEL, -m MODEL
                        Load model data
  --resume RESUME, -res RESUME
                        Resume the training from snapshot
  --root ROOT, -R ROOT  Root directory path of input image
  --training_list TRAINING_LIST
                        Path to training image list file
  --validation_list VALIDATION_LIST
                        Path to validation image list file
Example:
To train 3D Unet using gpu

python train.py -g 0
Prediction
To predict images with trained network.

python predict.py -h

optional arguments:
  -h, --help            show this help message and exit
  --gpu GPU, -g GPU     GPU ID (negative value indicates CPU)
  --base BASE, -B BASE  base directory path of program files
  --config_path CONFIG_PATH
                        path to config file
  --out OUT, -o OUT     Directory to output the result
  --model MODEL, -m MODEL
                        Load model data(snapshot)
  --root ROOT, -R ROOT  Root directory path of input image
  --test_list TEST_LIST
                        Path to test image list file
Example:
To predict label using gpu

python predict.py -g 0 -m results/training/UNet3D_150000.npz
Training result
Training loss and dice score.
loss
dice

Predicted result
Example of input image
input

Example of ground truth
gt

Example of prediction
p

Results
We calculated jaccard index of image shown above.

label	J.I.
0	0.99553
1	0.83438
2	0.86771
3	0.91392
4	0.80850
5	0.88321
6	0.87240
