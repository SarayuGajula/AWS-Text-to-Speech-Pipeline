# AWS Text-to-Speech Pipeline 🔊

This project converts text into speech using **Amazon Polly**, delivers the audio as an `.mp3` file via **Lambda**, and makes it publicly accessible through **Amazon S3**.

---

## 🛠️ How It Works

- ✅ Text is entered into a terminal command or through API Gateway
- ✅ API Gateway sends request to Lambda function
- ✅ Lambda:
  - Uses Polly to synthesize speech
  - Saves the audio MP3 in an S3 bucket
  - Returns a public URL
- ✅ Your terminal script plays the audio immediately

---

## 📂 Project Structure

aws-text-to-speech-pipeline/
├── lambda_function.py
├── text_to_speech.py
├── requirements.txt
├── demo/
│ └── aws_text_to_speech_terminal_demo.png
└── README.md

yaml
Copy
Edit

---

## 📷 Demo

![CLI Demo](demo/aws_text_to_speech_terminal_demo.png)

---

## 🧪 Usage (Local Script)

```bash
python3 text_to_speech.py "Hi"
Or use your terminal alias:

bash
Copy
Edit
speak "hello"
