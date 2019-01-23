# FloWaveNet : A Generative Flow for Raw Audio 

# Requirements

- PyTorch 0.4.1
- Python 3.6
- Librosa

# Examples

#### Step 1. Download Dataset

- LJSpeech : [https://keithito.com/LJ-Speech-Dataset/](https://keithito.com/LJ-Speech-Dataset/)

#### Step 2. Preprocessing (Preparing Mel Spectrogram)

`python preprocessing.py --in_dir ljspeech --out_dir DATASETS/ljspeech`

#### Step 3. Train

`python train.py --model_name flowavenet --batch_size 2 --n_block 8 --n_flow 6 --n_layer 2 --num_gpu 1 --block_per_split 4`

#### Step 4. Synthesize

`--load_step CHECKPOINT` : the # of the pre-trained model's global training step (also depicted in the trained weight file)

`--temp`: Temperature (standard deviation) value implemented as z ~ N(0, 1 * TEMPERATURE)

ex) `python synthesize.py --model_name flowavenet --n_block 8 --n_flow 6 --n_layer 2 --block_per_split 4 --load_step 100000 --temp 0.8 --num_samples 10`
