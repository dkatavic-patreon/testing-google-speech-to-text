# Google Speech-to-Text

Experimented with Google Speech-to-Text during the inovation day for transcribing Patreon audio posts with the purpuse of content moderation

## How to run

1. Authenticate with Google and download application credentials
2. export ENV variable `export GOOGLE_APPLICATION_CREDENTIALS={PATH}`
3. install dependencies `pip install -r requirements.txt`
4. run `python transcribe.py`

## Findings

-   Need to download and upload the file or point it to the gcs link
-   Should be able to auto recognise the language but still haven't figure that out
-   Synchronous approach is not viable, it takes a long time to transcribe 1hr audio file
-   Sync upload rate limit: After 5 minute got google.api_core.exceptions.InvalidArgument: 400 Request payload size exceeds the limit: 10485760 bytes.
-   Getting empty transcribe responses on non wav files. Tried mp3, ogg, wav and webm
-   Only wav file worked
-   Transcript is very accurate on a male.wav file, with only 1 out of 150 words wrongly transcribed. confidence score was 0.6856182217597961
-   Had issue with setting sample_rate_hertz, there should be a way of automatically detecting it from the audio header file

## TODO

-   Test auto language detection
-   Test multiple voices
-   Test different audio formats used at Patreon
