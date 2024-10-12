🖥️ Chat Automation with PyAutoGUI & OpenAI
Welcome to Chat Automation, a Python project that combines the power of PyAutoGUI for automating GUI interactions with OpenAI's GPT-3.5 for generating clever, humorous chat responses. Perfect for automating chats, analyzing conversations, and adding a fun twist to messaging apps!

🚀 Features
Mouse Automation: Automatically clicks and drags to select text from chat windows.
Clipboard Integration: Copies chat history directly from the screen. 
AI-Powered Responses: Uses OpenAI to generate witty replies based on the chat history.
Python-Powered: Simple Python code with powerful libraries like pyautogui, pyperclip, and openai.
🛠️ Installation
Clone the repository:
bash
Copy code
git clone https://github.com/your-repo/chat-automation.git
Install the required dependencies: 
bash
Copy code
pip install pyautogui pyperclip openai
Set up your OpenAI API key:
python
Copy code
client = OpenAI(api_key="<Your API Key Here>")
🔧 How It Works
Selects Chat Text:

Automatically clicks on the chat window at specific coordinates.
Drags the mouse to select a block of chat messages.
Generates AI Response:

Copies the chat history.
Feeds it into OpenAI's GPT-3.5 to analyze the conversation.
Receives a funny, engaging response.
Posts Reply:

Pastes the AI-generated response into the chat.
Presses 'Enter' to send the message.
💻 Code Example
python
Copy code
import pyautogui
import pyperclip
import time
from openai import OpenAI

client = OpenAI(api_key="<Your API Key Here>")

def is_last_message_from_sender(chat_log, sender_name="Rohan Das"):
    messages = chat_log.strip().split("/2024] ")[-1]
    return sender_name in messages

pyautogui.click(1639, 1412)  # Click on chat window
time.sleep(1)

while True:
    time.sleep(5)
    pyautogui.moveTo(972, 202)
    pyautogui.dragTo(2213, 1278, duration=2.0, button='left')  # Drag to select text
    pyautogui.hotkey('ctrl', 'c')  # Copy text
    chat_history = pyperclip.paste()
    
    if is_last_message_from_sender(chat_history):
        completion = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a funny, witty coder who analyzes chats and gives humorous replies."},
                {"role": "user", "content": chat_history}
            ]
        )
        response = completion.choices[0].message.content
        pyperclip.copy(response)
        pyautogui.click(1808, 1328)  # Click to focus on message input
        pyautogui.hotkey('ctrl', 'v')  # Paste the AI response
        pyautogui.press('enter')  # Send message
✨ Demo
Check out how this script automates a real-time chat session with AI-generated responses:

[Insert Demo GIF/Screenshot]

🔍 More to Explore
Integrate with different chat platforms.
Add additional AI models for diverse responses.
Customize the automation to suit different workflows.
🤝 Contributing
Feel free to contribute, suggest features, or improve the code by submitting a pull request!

