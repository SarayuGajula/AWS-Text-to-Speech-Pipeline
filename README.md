# AWS Text-to-Speech Pipeline 🔊

This project converts text into speech using **Amazon Polly**, delivers the audio as an `.mp3` file via **AWS Lambda**, and makes it publicly accessible through **Amazon S3**. You can run it locally with a simple command or through an API Gateway integration.

---
Architecture

<img width="1373" height="629" alt="Screenshot 2026-01-19 at 4 47 11 PM" src="https://github.com/user-attachments/assets/6f1cfc9a-5cba-4da4-9e13-3356329455ab" />








## 🛠️ How It Works

- You enter text via terminal or API Gateway  
- API Gateway sends the request to Lambda  
- Lambda:
  - Uses Amazon Polly to synthesize speech
  - Stores the `.mp3` file in an S3 bucket
  - Returns a publicly accessible S3 URL  
- Terminal script plays the MP3 using `pydub`

---

## 💻 AWS Lambda Logic

Core logic used in Lambda function:

```python
response = polly.synthesize_speech(
    Text=text,
    OutputFormat="mp3",
    VoiceId=voice
)

audio_stream = response["AudioStream"].read()

s3.put_object(
    Bucket="s3-audio-archive",
    Key=filename,
    Body=audio_stream,
    ContentType="audio/mpeg"
)
```

---

## 📡 S3 Bucket Policy

To make your `.mp3` files publicly accessible, add this S3 bucket policy:

```json
{
  "Effect": "Allow",
  "Principal": "*",
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::s3-audio-archive/*"
}
```

Make sure you also disable **"Block Public Access"** in the S3 settings.

---

## 🔐 AWS Credentials Setup

Your AWS credentials are stored in `~/.aws/credentials` like this:

```
[default]
aws_access_key_id = YOUR_ACCESS_KEY
aws_secret_access_key = YOUR_SECRET_KEY
region = us-east-1
```

These are used by `boto3` to connect your script to AWS.

---

## 📦 Requirements

Install dependencies:

```bash
pip install -r requirements.txt
```

Contents of `requirements.txt`:

```
boto3
pydub
```

---

## 🧠 Built With

- Amazon Polly  
- AWS Lambda  
- Amazon S3  
- API Gateway  
- Python (`boto3`, `pydub`)
