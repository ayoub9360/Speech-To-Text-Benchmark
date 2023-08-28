# Speech To Text Performance Evaluation

Welcome to the Speech To Text Benchmark project! This initiative empowers you to rigorously assess and benchmark the Word Error Rate (WER) across various state-of-the-art Speech-to-Text (STT) models, offered by Google's and OpenAI's platforms.

## Installation and Configuration Guide

1. **Setting up Google Cloud Storage**: Begin by creating a new storage bucket on [Google Cloud Storage](https://pantheon.corp.google.com/storage/browser). Then, populate the bucket with the contents of the 'storage' folder.

2. **Google Workbench Setup**: Create a Google Workbench within your Google Cloud Project. Activate the [Workbench API](https://pantheon.corp.google.com/vertex-ai/workbench/user-managed). Next, configure the Workbench with the following parameters:

   - Operating System: Debian 11
   - Python Environment: Python 3 (including Intel® MKL support)

3. **Accessing the Notebook**: Launch the JupyterLab environment by selecting "OPEN JUPYTERLAB."

4. **Cloning the Repository**: Clone the repository into the environment:

   - Click on the 'Git' option in the top toolbar.
   - Choose 'Clone a Repository.'
   - Clone the repository located at "https://github.com/ayoub9360/Speech-To-Text-Benchmark.git".

5. **Installing Dependencies**: Open a terminal within the JupyterLab environment and execute the following commands:

   - `pip install google-cloud-speech`
   - `pip install -U openai-whisper`
   - `sudo apt update && sudo apt install ffmpeg`

6. **Generating Transcripts**: Navigate to `/Speech-To-Text-Benchmark/Notebooks/` and open a transcript generator. Update the bucket name as required, and execute the file to generate transcripts. Feel free to experiment with various models such as:

   - GCP Chirp model
   - GCP Long model
   - Whisper Tiny
   - Whisper Small
   - Whisper Base
   - Whisper Medium
   - Whisper Large

7. **Executing the Benchmark**: Run the `calculate_wer.ipynb` file. Detailed WER scores can be found in the `wer_diagnosis` folder.

## Conducting Tests on Additional Videos

If you wish to carry out comparative analyses on other video samples using different STT models, please follow the following instructions:

1. **Adding Audio Files**: Integrate the audio file you wish to assess into the folder of the Cloud Storage Bucket: `{Bucket}/source/chirp/audio/{Language}/{File-name}.flac`

2. **Incorporating Human Transcripts**: Include the human transcript in the folder: `{Bucket}/ground_truth/{File-name}.txt`

   - The file-name need to be the same as the video

3. **Transcript Generation**: Utilize the transcript generator in the notebook to produce transcripts.

4. **Executing the Benchmark**: Run the `calculate_wer.ipynb` file within the notebook.

## Results overview

As part of our benchmark, we meticulously evaluated a collection of videos. Here we present the full results obtained by subjecting this video dataset to our benchmarking process.

| **Video ID** | **chirp** |  **long** | **whisper_base** | **whisper_small** | **whisper_tiny** |
| -----------: | --------: | --------: | ---------------: | ----------------: | ---------------: |
|  **x58y7eg** |  3.501545 |  9.371782 |         8.650875 |          5.870237 |        12.564367 |
|  **x8mmzj2** |  8.323831 | 16.419612 |        24.401368 |         18.928164 |        33.751425 |
|  **x8mv7he** |  4.043127 |  8.355795 |        16.172507 |         12.398922 |        25.876011 |
|  **x8n0jf1** |  7.853403 | 13.403141 |        13.298429 |         11.413613 |        20.314136 |
|  **x8n29uv** |  8.125000 | 15.000000 |        12.500000 |         10.625000 |        13.125000 |
|  **x8n38du** |  7.594937 | 10.126582 |        15.189873 |         12.658228 |        29.113924 |
|  **x8n3e82** | 17.500000 | 35.000000 |        52.500000 |         40.000000 |       110.000000 |
|  **x8n3jhn** | 14.159292 | 11.061947 |        28.761062 |         18.584071 |        46.902655 |
|  **x8n3qv2** |  0.847458 |  1.694915 |         7.627119 |          2.542373 |        12.711864 |
|  **x8n3ssu** |  0.000000 |  0.000000 |      5800.000000 |          0.000000 |      5600.000000 |

Note: The values in the table represent Word Error Rate (WER) scores for the respective models on different video samples.
