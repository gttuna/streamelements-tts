# StreamElements TTS

A simple web-based Text-to-Speech tool using the StreamElements API with Brian voice.

**Live Demo:** https://gttuna.github.io/streamelements-tts/

## Background

This project is inspired by [5E7EN/TTS-Emulator](https://github.com/5E7EN/TTS-Emulator), which used the StreamElements TTS API without authentication. That approach no longer works as StreamElements now requires authentication for their speech endpoint.

## What Changed

The original TTS-Emulator made unauthenticated requests to:
```
https://api.streamelements.com/kappa/v2/speech?voice=Brian&text=...
```

StreamElements now requires a `key` parameter for authentication:
```
https://api.streamelements.com/kappa/v2/speech?voice=Brian&text=...&key=<authToken>
```

The `authToken` is extracted from your StreamElements JWT token (it's a field within the JWT payload).

## How to Use

1. Go to [StreamElements Dashboard](https://streamelements.com/dashboard/account/channels)
2. Navigate to **Account** → **Channels** → **Show secrets**
3. Copy your **JWT Token**
4. Paste it into the token field on the page
5. Enter your message and click **Speak**

The JWT token is saved in your browser's localStorage so you don't need to re-enter it each time.

## Features

- Brian voice TTS (English UK)
- Auto-saves your JWT token locally
- Download generated audio as MP3
- Character counter (500 char limit)
- Ctrl+Enter shortcut to submit

## Technical Details

The tool parses your JWT token to extract the `authToken` field from the payload, which is then used as the `key` query parameter for the StreamElements speech API.

## License

MIT
