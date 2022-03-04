---
title: 【在 LINE 中用語音訂飲料】從 Cloud Bucket 抓取檔案並呼叫 Speech-to-Text API
categories: Google
tags:
---


![](https://nijialin.com/images/2022/)

# 前言

- 讓 STT 去 bucket 抓
- 範例 code https://cloud.google.com/speech-to-text/docs/samples/speech-transcribe-async-gcs#speech_transcribe_async_gcs-python


```python
def transcribe_gcs(gcs_uri):
    """Asynchronously transcribes the audio file specified by the gcs_uri."""
    from google.cloud import speech

    client = speech.SpeechClient()

    audio = speech.RecognitionAudio(uri=gcs_uri)
    config = speech.RecognitionConfig(
        encoding=speech.RecognitionConfig.AudioEncoding.FLAC,
        sample_rate_hertz=16000,
        language_code="en-US",
    )

    operation = client.long_running_recognize(config=config, audio=audio)

    print("Waiting for operation to complete...")
    response = operation.result(timeout=90)

    # Each result is for a consecutive portion of the audio. Iterate through
    # them to get the transcripts for the entire audio file.
    for result in response.results:
        # The first alternative is the most likely one for this portion.
        print(u"Transcript: {}".format(result.alternatives[0].transcript))
        print("Confidence: {}".format(result.alternatives[0].confidence))
```

- m4a 與 mp3 介紹，m4a品質好，mp3 泛用，可以直接 m4a轉mp3
- 上傳到 Cloud Bucket

<!-- more -->


# 結論
