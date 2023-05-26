# Deep Learning Project 
# Group Code:F2022_07

## Install
This project requires Python 3.x and the following libraries installed:

Pandas

matplotlib

os

pickle

librosa

pydub

soundfile

io

Keras

Tensorflow

We got access to all of that by using Anaconda.

## Data Set Overview
Our classification and generation models were trained on a diverse data set of Arabic music. The data set was carefully curated to include a variety of genres, including classical, modern, piano, and oud songs, to ensure the model was exposed to a wide range of musical styles. The classical category consisted of compositions by renowned artists such as Mohamed Abdelwahab, Reyad ElSonbaty, and Balegh Hamdy. The modern category included songs by popular singers like Sherin Abd El-Wahab, Tarek Madkour, Mohamed Foad, Hesham Abbas, Fairouz, Waleed Saad, Nasir shama, Mohamed Rahem, and others. Additionally, the data set included piano compositions by Omar Khorshed and some oud songs. The model was also trained on compositions by Hamza Namira and Omar Khairat, two highly respected contemporary musicians.

To ensure consistency in the data set, all songs were preprocessed to a uniform length accordance to the model requirement. This allowed for a fair comparison between different genres and styles, as well as ensuring that the model was exposed to enough musical material to learn from. 

Overall, the data set used for training the music generation model was carefully selected to provide a diverse set of musical styles and genres while maintaining consistency in length. The data set and preprocessing methods used in this study can serve as a foundation for future music generation research in Arabic music and related fields.

## Data Collecting & Preprocessing.
We started by collecting Arabic music data for about 11 different composers, totaling approximately 256 files ranging from 3 to 55 minutes each. After collecting this vast amount of data, we began our first task, which involved preprocessing the data through a pipeline of tasks:

1- Segment the large files.

2- Convert them to WAV format.

3- Segment the WAV files into smaller pieces.

4- Normalize the audio data.

5- Extract MFCCs (Mel Frequency Cepstral Coefficients) in the form of NumPy arrays for the first and second experiments in the classification task.

6- Extract Mel-Spectrograms for the third, fourth, and fifth experiments and log-spectrograms for the generation task.

7- Plot the spectrograms to observe the trends.

## Classification task

For the classification task, we employed several approaches to improve the accuracy of our model. 

1- In the first experiment, we used non-evenly distributed data with MFCC as input and a model architecture consisting of two con2d layers to classify the data into 11 categories. This experiment resulted in a test accuracy of 0.5489.

2- In the second experiment, we modified the architecture used in the first experiment to achieve better validation and testing accuracy. Additionally, we used evenly distributed data in this experiment, which resulted in a higher test accuracy of 0.5595.


3- In the third experiment, we changed the form of the input to mel spectrograms, which are capable of representing more features, thereby aiding the model in learning and leading to improved results. This experiment resulted in a test accuracy of 0.7015. However, the validation accuracy was lower at 0.5925.

4- To further improve our model's accuracy, we used data augmentation techniques in the fourth experiment to increase the size of our data and repeated experiment three. This led to a better accuracy, with a test accuracy of 0.7316.


5- Finally, in the fifth experiment, we used the same approach as in experiment two but with an increase in the augmented data. This resulted in a significant improvement in accuracy, with a test accuracy of 0.8143.


### Our best experiment results " Experiment 5 Confusion Matrix ":
![WhatsApp Image 2023-05-23 at 2 48 33 PM](https://github.com/eshaarawy/Ai-Arabic-Music-/assets/109802881/706762ba-7bb0-4bd6-99e5-7dcbb156456e)

## Generation Task
1- Our data preprocessing involved a well-defined pipeline, starting with segmenting the audio files into 5.94-second intervals, padding if necessary, and extracting log spectrograms for model training. We then applied min-max normalization for post-processing and saved the preprocessed data in the specified paths. As an additional step, we also extracted log spectrogram images to observe music trends in terms of frequency and time. In total, we preprocessed 75 WAV files, resulting in 8756 segments.

2- In order to generate new music data from our classical music dataset, we employed a Variational Autoencoder (VAE) architecture. The VAE consisted of three main components: an Encoder, a Bottleneck, and a Decoder.

The Encoder and Decoder were constructed using five convolutional layers each, resulting in a substantial number of model parameters. To train the model, we utilized a two-step process. We initially set the learning rate to 0.00005 and trained the model for approximately 90 epochs. Afterwards, we adjusted the learning rate to 0.00009 and continued training for the remaining epochs.

The results we obtained from the trained VAE were highly promising. To evaluate the quality of the generated music, we conducted a subjective assessment by having ten individuals listen to both the original music samples and the generated samples. The feedback we received from the listeners indicated that the generated samples closely resembled the original ones.

Furthermore, we assessed the reconstruction accuracy and the Kullback-Leibler (KL) divergence loss, both of which confirmed the high quality of the generated music.
### The loss when starting fitting:
![res_1](https://github.com/eshaarawy/Ai-Arabic-Music-/assets/109802881/cc262539-7ad7-40a9-8fad-9c6b34d88a53)
### The promising results after fitting the model given 90 epochs:
![Capture](https://github.com/eshaarawy/Ai-Arabic-Music-/assets/109802881/11585f54-d71d-4e9a-9b32-0ba28ebc6a72)

For more comprehensive information about our results, the architecture of the model, and the post-processing techniques applied, please refer to the files provided in the repository.

You could find below two images:

### Output: Generated features in the form of spectrogram imag(Generation Model
![WhatsApp Image 2023-05-07 at 7 59 19 PM](https://github.com/eshaarawy/Ai-Arabic-Music-/assets/109802881/3e233cd0-ed75-4876-a401-6b43dd4d0dbe)

### Input : original extracted feature in the form of spectrogram image (Generation Model)
![WhatsApp Image 2023-05-07 at 7 59 51 PM](https://github.com/eshaarawy/Ai-Arabic-Music-/assets/109802881/14366ebd-e46f-4886-bb5e-9b67a0aff822)

