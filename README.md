# Transcribe multiple MP3-files with Whisper regardless of their size #

Hi!

This project aims to assist individuals struggling to find a way to utilize the Whisper 1 API from the OpenAI platform for transcribing multiple files.
Please note that the Whisper 1 API is no longer the most efficient way for using Whisper, as there are ow the whisper-3 model on HuggingFace and Whisper JAX. The Whisper 1 API may take approximately 1 min or more to transcribe a 300 MB mp3-file. 
Depending on the total size of the mp3 files in your directory, this script could run for several minutes or even hours. If possess strong programming skills and are capable of setting up the necessary requirements for using these methods, consider switching.
This project serves merely as a demonstration for a client who sought a straightforward and easy script.

There are multiple challenges encountered when:
1. Transcribing multiple files without repeatedly calling the function for each file (this requires a script with loops to navigate through the directory, etc.).
2. Handling any file larger than ~20 MB. OpenAI states that the maximum file size is 25 MB, but experience with this project has shown that files around 20 MB can also cause the script to halt transcription and disconnect from the API which results in the transcription to stop.

! Through testing with different maximum file sizes, I found out that chunking mp3 files larger than 10 MB into segments of 10 MB or less allows the script to run perfectly fine
--> This batch processing method makes it possible to sequentially transcribe an entire directory of multiple files, even for files as large as 300 MB, by just running the script once
--> The script automatically saves the transcriptions as text files in a subfolder within your audio file directory and deletes all the chunked segmented files after transcribing them
--> you are left with the same directory you started with plus a neatly organized folder containing the transcription files
--> the transcription files are easy to identify as they retain the same names of their original audio files


The following libraries are needed to run this script / project:

- openai (for using the Whisper API client)
- pydub for loading audio files (easiest method out there)
( - os and dotenv for using environment variables if you don't want others to see your private API access key)


The code is explained through comments within the Jupyter Notebook.


____________________________________

Take a look at the test files if you want to see some example results.
