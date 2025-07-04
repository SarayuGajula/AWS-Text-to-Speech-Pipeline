# AWS Text-to-Speech Pipeline 🔊

This project converts text into speech using **Amazon Polly**, delivers the audio as an `.mp3` file via **Lambda**, and makes it publicly accessible through **Amazon S3**.

## 🛠️ How It Works

- API Gateway receives text input from the client
- Triggers a Lambda function that:
  - Uses **Polly** to synthesize speech
  - Uploads the `.mp3` to a public **S3 bucket**
  - Returns the audio file's URL to the client
- You can run a Python script to instantly hear the result

---

## 📂 Folder Structure

