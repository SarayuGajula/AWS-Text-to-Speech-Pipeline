# AWS Text-to-Speech Pipeline 🔊

This project converts text into speech using **Amazon Polly**, delivers the audio as an `.mp3` file via **AWS Lambda**, and makes it publicly accessible through **Amazon S3**. You can run it locally with a simple command or through an API Gateway integration.

---

## 🛠️ How It Works

- ✅ You enter text via terminal or API Gateway
- ✅ API Gateway sends the request to Lambda
- ✅ Lambda:
  - Uses Amazon Polly to synthesize speech
  - Stores the `.mp3` file in an S3 bucket
  - Returns a publicly accessible S3 URL
- ✅ Terminal script plays the MP3 using `pydub`






