# Ai_Chatbot
This Python code is a project i designed to create a voice-interactive AI chatbot that combines speech recognition, a language model, and text-to-speech synthesis. The chatbot listens to user input through a microphone, generates a text-based response using a language model, and then vocalizes this response, creating a seamless conversational experience. Here's a detailed breakdown of how it works and the role of each component:

  1. TTS Engine Initialization (pyttsx3): 
The script begins by initializing the text-to-speech (TTS) engine using the pyttsx3 library. This engine is responsible for converting the AI's text responses into speech, allowing the chatbot to communicate audibly with the user. The TTS engine is versatile and can be configured to use different voices and adjust parameters such as speed and volume, though these features are not explicitly modified in this code.

 2.  Speech Recognition (speech_recognition library): 
The code sets up a speech recognizer using the speech_recognition library, which enables the chatbot to listen to and interpret spoken language from the user. The recognizer uses the Google Web Speech API to transcribe the audio input into text. The transcription process is encapsulated in a loop that continuously listens for user input through the microphone. If the recognizer encounters any issues, such as unclear speech or a problem with the API, it handles these exceptions gracefully, prompting the user to try again.

 3. Language Model Setup (OllamaLLM): 
The core of the chatbot's intelligence comes from the OllamaLLM language model, a part of the langchain_ollama package. The model is initialized with a specific variant, "llama3", which is designed to understand and generate human-like text. 

   ● Template Definition: The script defines a conversation template using ChatPromptTemplate from langchain_core.prompts. This template outlines how the conversation should be structured, with placeholders for the ongoing conversation history (context) and the user’s latest question (question). The template ensures that each AI response is contextualized based on the entire conversation, allowing for more coherent and relevant replies.

   Prompt Creation: The template and the language model are combined into a processing chain. This chain allows the chatbot to generate a response by invoking the model with the current conversation history and the user's latest input. The language model plays a crucial role by leveraging its understanding of natural language to generate meaningful, context-aware responses.

  4. Interactive Conversation Flow
   • Listening and Transcribing: In the main loop of the handle_conversation function, the program listens for user input through the microphone. Once the speech is captured, the recognizer transcribes it into text, which is then displayed in the console for feedback.

   ●  Generating a Response: The text input from the user is fed into the language model via the prompt chain. The OllamaLLM model processes the input, considering the ongoing conversation's context, and generates a response. This context-aware generation allows the chatbot to engage in more natural and meaningful dialogue.

   ● Speaking the Response: After generating a response, the script uses the pyttsx3 TTS engine to convert the AI's text-based response back into speech. This is then vocalized, providing the user with an audible reply.

   ●  Context Management: The conversation history (context) is updated with each interaction, appending the user’s input and the AI’s response. This ongoing context helps the language model maintain continuity in the conversation, allowing it to refer back to previous exchanges and provide more informed responses.

●  Exit Condition
The loop is designed to run indefinitely, continuously listening for and responding to user input. The interaction only ends when the user explicitly says "exit," which breaks the loop and terminates the program.

 ● Role of OllamaLLM
The OllamaLLM language model is central to the functionality of this chatbot. It is basically the (BRAIN) of the whole code, it is responsible for understanding the user's questions and generating coherent, context-aware responses. By integrating the model with a template that includes the conversation history, the chatbot can provide more personalized and relevant answers, making the interaction feel more natural. The model's ability to process complex language and maintain context across multiple exchanges is what allows this chatbot to simulate a realistic conversation.

In summary, this code effectively combines speech recognition, a powerful language model, and text-to-speech synthesis to create a dynamic, voice-interactive chatbot. The OllamaLLM model is key to generating intelligent, contextually relevant responses, making the chatbot a versatile tool for various applications, from personal assistants to customer service bots.
