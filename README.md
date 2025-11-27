# Automatic multimodal question and answering for video lectures

**Presentation:** [Canva]([https://www.canva.com/design/DAGhsnSEdRo/IxsYfXwTJMAf6B7icCmBbQ/view?utm_content=DAGhsnSEdRo&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=hb2715aa87e](https://www.canva.com/design/DAG56O5shlc/3wjqxLLnbtI-f63GOJ2v2w/edit?utm_content=DAG56O5shlc&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton))

**Demo:** [Youtube]([https://www.youtube.com/watch?v=EWW-C-lGbvo](https://www.youtube.com/watch?v=lutgSkiieJ4))

## Project description
This work involves synthesizing a video from a set of video lectures that answers the question raised by the student. This contains following objectives.
1. Select a video lectures set that containing SRTs.
2. Study and implement the voice activity detection (VAD) algorithm.
3. Extract the speech segments from the VAD output.
4. Identify the spoken content in text form using ASR for each segment.
5. Obtain the sentence specific time stamps.
6. Create answer summary.
7. Identify video parts corresponding to the answer summary.
8. Stitch the summary video segments to obtain natural like video.

## Guide
Chiranjeevi Yarra (Spoken Language Forensics & Informatics (SLFI) group - LTRC)

## Running the Frontend
* We used Flask, HTML to run frontend server. To run
1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```
2. Run
    ```bash
    python3 main.py
    ```

## Video to Audio Conversion and Dividing Audio into Audio Chunks
### Prerequisities
1. FFMPEG:  `pip3 install ffmpeg-python`
2. PyTorch: `pip3 install torch torchvision`
3. Transformers: ` pip3 install transformers`
4. Sentence Transfomers: `pip3 install -U sentence-transformers`
5. Faiss: `pip3 install faiss-cpu`
6. Silero VAD: `pip3 install silero-vad`
7. SoundFile: `pip3 install soundfile`
8. Sox: `pip3 install sox`
9. Streamlit: `pip3 install streamlit`
10. pysrt: `pip3 install pysrt`
11. moviepy: `pip3 install moviepy==1.0.3`

* Note: We require `ffmpeg` in system also.
So please install through `apt install ffmpeg` (Linux) or `brew install ffmpeg` (Mac)

### Steps
* Videos should be in Data/ Folder. 
1. Run the following notebook to complete the processing up to audio chunk generation:

**`pipeline-qwen.ipynb`**

This notebook will:
- Convert Video → Audio  
- Perform Voice Activity Detection (VAD)  
- Generate Audio Chunks  
* This will generate Audio Chunks (.wav) files for each lectures.

2. Converting Audio Chunks into SRT files using Whisper model and MFA.
3. Encode this SRT files using QWEN model by running `Encoding.py` file.
4. Now, the generated `.index` files use in the backend repo to use with backend.



## Question Classifier Output
![Classify Question Image](assets/Classify-Question.png)

## Finding Related Sentences for Question Output
![Related Sentences output](assets/Related-Sentences-Output.png)

## Voice Activity Detector Output
![Voice Activity Detector Output](assets/Voice-Activity-Detector-Output.png)
