# AI Meeting Assistant

A Google Colab-based speech-to-text meeting assistant. The notebook accepts an audio recording, transcribes it with OpenAI Whisper, normalizes financial terminology, and uses an OpenRouter-hosted language model to generate meeting minutes and an actionable task list.

> **Note:** This project is speech-to-text, not text-to-speech. It does not save the raw transcription as a text file. Instead, it saves the generated meeting minutes and tasks to `meeting_minutes.txt` while also displaying the result in the Gradio interface.

## Features

- Upload an audio file through a Gradio interface.
- Transcribe speech using `openai/whisper-tiny.en`.
- Expand and normalize financial acronyms and terminology.
- Generate meeting minutes, decisions, and task items.
- Download the generated output as a text file.

## Requirements

- Python 3
- Google Colab or a local Jupyter environment
- An OpenRouter API key configured in the environment
- Internet access to download the Whisper model and call OpenRouter

## Usage

1. Open [`Speech-to-Text.ipynb`](./Speech-to-Text.ipynb) in Google Colab.
2. Run the installation cells and configure your OpenRouter credentials.
3. Run the notebook cells in order.
4. Upload a meeting audio file in the Gradio interface.
5. Review the generated meeting minutes and tasks, then download `meeting_minutes.txt`.

You can also open the notebook directly in Colab:

[Open in Google Colab](https://colab.research.google.com/github/Danial-071/Text-to-Speech-/blob/main/Speech-to-Text.ipynb)

## Processing Workflow

1. Download or upload an audio recording.
2. Convert speech to text with Whisper automatic speech recognition.
3. Remove non-ASCII characters from the transcription.
4. Improve financial terminology using an LLM prompt.
5. Generate structured meeting minutes and tasks with LangChain.
6. Display and save the final result as a downloadable text file.

## Important Configuration Notes

- Install `langchain-openrouter` in addition to the packages currently listed in the notebook.
- Set the `OPENROUTER_API_KEY` environment variable before creating the `ChatOpenRouter` client.
- The notebook currently contains a model-name typo in `transcript_audio`; use the Whisper model (`openai/whisper-tiny.en`) for transcription.
- The default output path is `/content/meeting_minutes.txt`, which is suitable for Google Colab.
- Whisper Tiny English is lightweight and fast, but larger Whisper models may provide better accuracy.

## Limitations

- The transcription model is configured for English audio.
- Output quality depends on audio quality, model availability, and the language model response.
- Generated meeting minutes and task assignments should be reviewed for accuracy.
- The notebook is configured primarily for Google Colab and may require path and environment changes when run locally.

## License

No license has been specified for this project.
