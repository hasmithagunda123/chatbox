<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>HR Process Optimization</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #925f7e;
    }

    #chat-container {
      max-width: 600px;
      margin: 20px auto;
      background-color: #fff;
      border-radius: 10px;
      box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
      overflow: hidden;
    }

    .message-container {
      max-height: 300px;
      overflow-y: scroll;
      padding: 10px;
    }

    .message {
      margin-bottom: 10px;
      padding: 10px;
      border-radius: 8px;
    }

    .user-message {
      background-color: #3498db;
      color: #fff;
      text-align: right;
    }

    .bot-message {
      background-color: #e1e1e1;
    }

    .user-input {
      display: flex;
      align-items: center;
      padding: 10px;
    }

    #userInput {
      flex: 1;
      padding: 8px;
      border: none;
      border-radius: 4px;
      margin-right: 8px;
    }

    #sendButton {
      padding: 8px 16px;
      border: none;
      border-radius: 4px;
      background-color: #3498db;
      color: #fff;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    #sendButton:hover {
      background-color: #267dbd;
    }
  </style>
</head>
<body>
  <div id="chat-container">
    <div id="messages" class="message-container"></div>
    <div class="user-input">
      <input type="text" id="userInput" placeholder="Type your message...">
      <button id="sendButton">Send</button>
    </div>
  </div>

  <script>
    const messagesDiv = document.getElementById('messages');
    const userInput = document.getElementById('userInput');
    const sendButton = document.getElementById('sendButton');

    // Function to add a message to the chatbox
    function addMessage(text, isUser = false) {
      const messageDiv = document.createElement('div');
      messageDiv.className = isUser ? 'message user-message' : 'message bot-message';
      messageDiv.textContent = text;
      messagesDiv.appendChild(messageDiv);

      // Automatically scroll to the bottom of the chat
      messagesDiv.scrollTop = messagesDiv.scrollHeight;
    }

    // Function to simulate a bot response
    function simulateBotResponse(userMessage) {
      const botResponse = `Bot: Thank you for your message: "${userMessage}". I'm here to help with HR processes. provide your gmail for further.`;
      addMessage(botResponse);
    }

    sendButton.addEventListener('click', () => {
      const userMessage = userInput.value;
      if (userMessage) {
        addMessage(`You: ${userMessage}`, true);
        simulateBotResponse(userMessage);
        userInput.value = '';
      }
    });

    // Handle pressing Enter key to send message
    userInput.addEventListener('keydown', (event) => {
      if (event.key === 'Enter') {
        sendButton.click();
        event.preventDefault();
      }
    });
  </script>
</body>
</html>
