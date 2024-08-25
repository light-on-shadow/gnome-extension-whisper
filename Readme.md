# Whisper Recorder GNOME Shell Extension

Whisper Recorder is a GNOME Shell extension that allows users to record audio directly from their microphone and transcribe it using OpenAI's Whisper API. The extension is designed to be lightweight and easy to use, providing a simple icon in the top bar to control recording and transcription.

## Features

- **One-click recording**: Start and stop recording audio from the microphone with a single click.
- **Real-time timer**: Display a timer in the top bar while recording to track duration.
- **Automatic transcription**: Send recorded audio to the OpenAI Whisper API for transcription.
- **Configurable API endpoint**: Customize the API endpoint used for transcription, including the ability to host the Whisper API locally.
- **FFmpeg integration**: Automatically converts recorded WAV files to M4A format if `ffmpeg` is installed, saving bandwidth during transcription uploads.
- **In-progress indicator**: Shows an in-progress icon while transcription is being processed.

## Installation

### Prerequisites

- **GNOME Shell 45+**: Ensure that your system is running GNOME Shell version 45 or later.
- **FFmpeg**: (Optional) Install `ffmpeg` if you want the extension to convert WAV files to M4A before uploading. On Debian-based systems, you can install it using:

  ```sh
  sudo apt-get install ffmpeg
  ```

### Installing the Extension

1. **Download or clone this repository**:

   ```sh
   git clone https://github.com/DominicBoettger/gnome-extension-whisper.git
   ```

2. **Copy the extension to your GNOME Shell extensions directory**:

   ```sh
   mkdir -p ~/.local/share/gnome-shell/extensions/whisper@DominicBoettger
   cp -r gnome-extension-whisper/* ~/.local/share/gnome-shell/extensions/whisper@DominicBoettger/
   ```

3. **Enable the extension**:

   Use GNOME Tweaks or the Extensions app to enable the Whisper Recorder extension.

4. **Restart GNOME Shell**:

   Press `Alt + F2`, type `r`, and press `Enter` to restart GNOME Shell.

## Usage

1. **Recording Audio**:
   - Click on the microphone icon in the top bar to start recording.
   - The icon will change to red, and a timer will display the elapsed recording time.

2. **Stopping Recording**:
   - Click the icon again to stop recording. The icon will change to a spinning gear to indicate that the transcription is in progress.

3. **Transcription**:
   - The recorded audio is automatically sent to the OpenAI Whisper API for transcription.
   - The transcribed text is copied to your clipboard and a notification confirms the completion.

4. **Preferences**:
   - Open the GNOME Extensions settings and select Whisper Recorder.
   - Set your OpenAI API key and (optionally) the API endpoint.
   - Your settings are saved automatically, and you can start recording immediately.

## Hosting Whisper API Locally

The Whisper Recorder extension allows you to change the API endpoint, enabling you to host the Whisper API locally. This is useful for:

- **Privacy**: Keep all data within your network.
- **Performance**: Reduce latency by avoiding external API calls.

### Steps to Host Whisper API Locally

1. **Set Up Your Local Environment**:
   - Set up the Whisper API on your local server. Follow the documentation provided by the API's developers to deploy it on your local machine or network.

2. **Update the API Endpoint**:
   - Open the preferences for Whisper Recorder and update the API endpoint to point to your local server (e.g., `http://localhost:8000/v1/`).

3. **Start Using the Extension**:
   - After setting the local endpoint, the extension will send the recorded audio to your locally hosted Whisper API for transcription.

## Development

If you are interested in contributing to the development of this extension, here are some useful commands and practices.

### Debugging the Extension

To debug the extension, you can run GNOME Shell in a nested Wayland session with debugging enabled:

```sh
export MUTTER_DEBUG_DUMMY_MODE_SPECS=1920x1080
export G_MESSAGES_DEBUG="GNOME Shell"
dbus-run-session -- gnome-shell --nested --wayland
```

This setup allows you to test and debug the extension without affecting your main GNOME Shell session. It runs GNOME Shell in a virtual environment with a resolution of 1920x1080.

### Common Issues

- **Icon doesn't change when clicking**: Ensure that the extension is enabled and that GNOME Shell is properly restarted.
- **No transcription received**: Verify that your API key is correct and that the API endpoint is reachable.
- **File conversion fails**: Check that `ffmpeg` is installed and accessible in your system's PATH.

### Debugging Logs

To view detailed error messages and logs, use the GNOME Shell Looking Glass tool:

1. Press `Alt + F2`, type `lg`, and press `Enter`.
2. Check the "Extension" tab for errors related to Whisper Recorder.

### Contributing

We welcome contributions to the Whisper Recorder GNOME Shell extension. To contribute:

1. **Fork the repository**.
2. **Create a new branch** for your feature or bugfix:

   ```sh
   git checkout -b my-feature-branch
   ```

3. **Make your changes**.
4. **Test thoroughly** to ensure your changes do not introduce bugs.
5. **Commit your changes** with a descriptive message:

   ```sh
   git commit -m "Add feature XYZ"
   ```

6. **Push to your fork**:

   ```sh
   git push origin my-feature-branch
   ```

7. **Create a pull request** against the `main` branch of this repository.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Thanks to the GNOME and OpenAI teams for their incredible work that makes projects like this possible.
- Inspired by the ease of voice recording and transcription with modern tools.

## Contact

For questions or support, please open an issue on the GitHub repository