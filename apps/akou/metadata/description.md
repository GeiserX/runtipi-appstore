akou turns audio into text on your own server. A program uploads a file, gets a job id back at once, and reads the result with text, language, word and segment times and speaker labels, by long-poll, by an event feed or by a signed webhook. It also answers the OpenAI transcription endpoint (`POST /v1/audio/transcriptions`), so clients that speak it work with no code on their side. Results come as text, JSON, SRT or VTT.

The default `fast` preset runs NVIDIA Parakeet TDT 0.6B v3 on the CPU, with Nemotron speaker labels when a job asks for them. The models download on the first job, about 3 GB.

## First use

1. Set the web page's admin password from a shell on the Runtipi host, at least 12 characters:

   `printf '%s' 'your-password' | docker exec -i akou akou admin set-password`

2. Open akou, log in, and create one API key per program on the Keys page. A key is shown once; give it to the program as its bearer token.

akou has no TLS of its own. Reach it through Runtipi's HTTPS address when you expose it.

Docs: https://geiserx.github.io/akou/server/
