.Assignment 7
-------------

⚠️This README concerns specifically the files and changes made as part of Assignment 4 for the Programming for Voice Technology course, part of the Voice Technology MSc of the Rijksuniversiteit Groningen.

The goal of the assingment is to run the notebook tutorial on training an STT model with your own voice. The tutorial requires the recording of at least a 100 clips in the Mozilla Common Voice platform. This data is then used to finetune a pre-trained English STT model. 

The tutorial notebook could not run because an error would occur when trying to initialize the data preformating -- ```RuntimeError: Missing checkpoint directory (--checkpoint_dir or --save checkpoint_dir)```. After reading thorugh the 🐸STT documentation and some trial-and-error, I fixed the issue by always specifying an (appropriate) directory for checkpoint loading and saving when initializing a process, even if the process does not involve checkpoints (like in the case of the data preformating). This solved the error and I was able to run the notebook through.

Additionaly, the notebook required two URLs through which a zipped folder with the mp3 files and a metadata text file with the sentences text would be downloaded. These links expire after 12 hours, which renders it inefficient for replication of the tutorial with my own data. Therefore, I edited the tutorial notebook to contain code that mounts a Google Drive and then places the folder and file where they are needed in the Collab session files. 

I was able to achieve slightly better results when testing the finetuned model on my own voice. The loss of the pretrained English model without finetuning is **29.283417**, whereas the finetuned model performs somewhat better with a loss of **27.602955**.

Running the tutorial with my data
-----------------------------------

From the 'notebooks' folder in this repository, download 'Assingment_7_Victoria.ipynb'. This is the edited tutorial notebook. The original is titled 'train-personal-model-with-common-voice.ipynb'and is located in the same 'notebooks' folder. Save the edited notebook in your Google Drive. **Do not upload it in a subfolder -- place it in the main Drive folder.**

The GitHub repository also contains a folder 'data_Victoria_finetuning', which has a 'takeout_441_pt_0.zip' folder and a 'takeout_441_metadata.txt' file. These are the audio files and the sentence text. **Upload them to your Google Drive main folder seperately (not in a subfolder together), where the notebook is also located.**

All dependencies will be installed when running the notebook. Noteably, SoX and Tensorflow are required. The code in the notebook de-installs your current Tensoflow installation and installs the 1.15 version which is the working version. A 'requirements.txt' is located in the 'notebooks' folder and it contains all dependencies specifically for 'Assignment_7_Victoria.ipynb'.

The notebook contains detailed descriptions on the steps of the process (including the data download and its upload to Drive). Beyond these steps, you need to just run the notebook cells and watch the magic happen!✨

Running the tutorial with your own data
----------------------------------------

Similarly, download the notebook and upload to your Drive (*as instructed above*). The notebook contains detailed intructions on how to download your data from Common Voice. For clarity, they are repated here:

* To download data from Common Voice, you need to have a Common Voice account and you must have recorded some sentences. Log-in or Sign-up in the top right corner of [commonvoice.mozilla.org](https://commonvoice.mozilla.org).

* Once you've logged in, you will see your username and avatar in the top right corner.

* From the drop-down menu next to your username, click on "Profile".

* Next, click the "Download My Data" button.

* Next, click the "Download" button.

* You should see a download page with two connections you can click on: Zip #1 of 1 and Sentence Text. Clicking on the first will download a zipped folder with all the mp3 files you recorded and the second will download a metadata text file with the text transcription of your recordings. This is all you need to finetune the model!

* Upload the zipped folder and the metadata text (*seperately, not in one subfolder together*) to the Drive where you saved this notebook.

Once again, this was all the ard work! From here on, simply run the code cells and see the model being finetuned to your own voice!✨


Information on 🐸STT
---------------------

**Coqui STT** (🐸STT) is a fast, open-source, multi-platform, deep-learning toolkit for training and deploying speech-to-text models. 🐸STT is battle tested in both production and research 🚀

🐸STT features
---------------

* High-quality pre-trained STT model.
* Efficient training pipeline with Multi-GPU support.
* Streaming inference.
* Multiple possible transcripts, each with an associated confidence score.
* Real-time inference.
* Small-footprint acoustic model.
* Bindings for various programming languages.

`Quickstart <https://stt.readthedocs.io/en/latest/#quickstart>`_
================================================================
