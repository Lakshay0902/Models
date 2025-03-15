# Running without ollama locally 

Manually find and download model from hugging face 
use transformers to run model in our system 
Manual optimization of the hardware 



# Running with ollama 

just install ollama and run model there 

Generally Run with docker container 

Docker Container  standadized boxes for your software 
It includes apps, code , dependencies and settings 
In runs same way on any computer 
Apps in container dont intefere with each other or main system 

Example : 
Chatbot app that uses llama2 
You'd need to install Ollama, CUDA drivers, manage python versions 
Your teammate on windows might face different setup issues 

With docker : 
You write a dockerFile( a blueprint of the container)
docker-compose up 

Ollama terms : 
Image : pre packaged snapshot of Ollama + its dependencies 
Container : running instance of the ollama image 
Volume  Storage to save models/data permanently 
Port mapping : talk to ollama via localhost:11434 


Steps : 
Install Ollama in windows https://ollama.com/
ollama pull Deepseek-r1:1.5b 
ollama run Deepseek-r1:1.5b
ollama serve // for running inside the server, check if any other ollama server is already running or opened in the taskbar or up arrow in the taskbar below 
the ollama server runs on http and not https , so https might give SSL error 
ollama rm model_name : delete the model 

Features : 
Streaming Feature 
if stream=True 
for chunk in response.iter_lines()  
print(chunk.decode("utf-8"))

Vision Models 
"images" : [base64_encoded_image]

Parameters 
json = {
     "model" : "deepseek-r1:1.5b"
     "prompt" : 
     "temperature" :
     "max_tokens" : 
     "top_p" : 
}

Multi-turn conversations with context retention 
/chat - maintains context through the messages array 
json = {
    "model" : "deepseek-r1:1.5b"
    "messages" : [
        {"role" : "user", "content" : "what is photosynthesis.."}
        {"role" : "assistant", "content" : "The process plants use.."}
        {"role" : "user" , "content" : "Explain it in simple terms"}
        {"role" : "system", "content" : "You are sarcastic assistant"}
    ]
}
/generate : for single time interactions 
json = {
    "model" : "deepseek-r1:1.5b"
    "system" : "You are sarcastic assistant"
    "prompt" : "xxx"
}


CREATING OWN MODEL WITH THE EXISTING ONE 
FROM deepseek-r1:1.5b 
SYSTEM "You are a sarcastic assistant. LearnOutcomes for different : {info}" 

ollama create mymodel -f mymodel.Modelfile 
ollama run mymodel










