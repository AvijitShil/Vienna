# Vienna
Vienna: Realtime voice AI assistant built with Python, LiveKit, Deepgram, GPT-4.1 &amp; Cartesia TTS. Features autonomous actions, medical guidance, strong privacy, and customizable cloned voices (including mine). Deployable anywhere—ideal for agentic healthcare &amp; productivity.

A highly intelligent, real-time voice AI assistant specializing in medical conversations with autonomous capabilities and custom voice cloning
Features • Installation • Usage • Architecture • API Reference
</div>

📋 Overview
Vienna is a cutting-edge voice AI assistant powered by LiveKit Agents framework, designed specifically for medical interactions with Indian English support. Built by Avijit, Vienna combines advanced speech recognition, natural language processing, and text-to-speech synthesis to deliver a conversational, witty, and highly capable AI assistant.
🎯 Key Highlights

🏥 Medical-Grade STT: Deepgram Nova 3 Medical model for accurate medical terminology
🇮🇳 Indian English Support: Optimized for Indian accents and dialects (en-IN)
🧠 GPT-4.1 Mini Intelligence: Fast, efficient responses with advanced reasoning
🎤 Custom Voice Cloning: Speaks in creator's own cloned voice for personalized experience
🗣️ Natural Voice Synthesis: Cartesia Sonic 3 TTS with fully customizable voice options
🛠️ Autonomous Actions: Web search, automation, email, weather, and more
⚡ High-Performance VAD: Precise voice activity detection with low latency
🎙️ Real-time Processing: Low-latency voice interactions with preemptive generation
🔇 Noise Cancellation: Built-in background voice cancellation (BVC)


✨ Features
🎙️ Voice & Speech Processing
FeatureTechnologyDescriptionSpeech-to-TextDeepgram Nova 3 MedicalMedical-grade transcription with Indian English supportText-to-SpeechCartesia Sonic 3Custom voice cloning - speaks in creator's own voiceVoice Activity DetectionSilero VAD/TurnDetectorHigh-performance, accurate detection with minimal latencyNoise CancellationLiveKit BVCReal-time background noise removalVoice Customization✅ Fully CustomizableClone any voice or use preset voices
🤖 AI Capabilities

Conversational Intelligence: GPT-4.1 Mini for fast, accurate responses
Medical Knowledge: Specialized in health-related conversations
Context Awareness: Maintains conversation history and context
Preemptive Generation: Responds while user is still speaking for faster interactions
Dry Humor & Personality: Engaging, witty responses without being sarcastic

🛠️ Autonomous Tool Functions
Vienna can perform various autonomous actions through integrated function tools:
🌐 Web & Information
python✅ open_website(url)          # Open any website
✅ search_web(query)          # Perform web searches
✅ get_news(topic)            # Fetch latest news
✅ get_stock_price(symbol)    # Check stock/crypto prices
⏰ Time & Weather
python✅ get_datetime()             # Current date and time
✅ lookup_weather(location)   # Real-time weather info
📧 Communication
python✅ send_email(to, subject, body)  # Send emails
✅ read_emails(count)             # Read unread emails
📍 Location Services
python✅ find_nearby_places(type)   # Find restaurants, ATMs, hospitals, etc.

🏗️ Architecture
┌─────────────────────────────────────────────────────────────────┐
│                        VIENNA AI PIPELINE                       │
└─────────────────────────────────────────────────────────────────┘

User Voice Input
      ↓
┌─────────────────┐
│ Noise Cancel.   │ ← LiveKit BVC (Background Voice Cancellation)
└────────┬────────┘
         ↓
┌─────────────────┐
│ Voice Activity  │ ← Silero VAD / TurnDetector
│   Detection     │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Speech-to-Text  │ ← Deepgram Nova 3 Medical (en-IN)
└────────┬────────┘
         ↓
┌─────────────────┐
│ LLM Processing  │ ← GPT-4.1 Mini (with function tools)
│ + Tool Calling  │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Text-to-Speech  │ ← Cartesia Sonic 3
└────────┬────────┘
         ↓
   Voice Output
System Components

Agent Session Manager: Orchestrates the entire voice pipeline
STT Engine: Converts speech to text with medical vocabulary support
LLM Core: Processes queries and decides when to use tools
Function Tools: 10+ autonomous action capabilities
TTS Engine: Generates natural-sounding voice responses
Metrics Collector: Monitors performance and usage statistics


🚀 Installation
Prerequisites

Python 3.8 or higher
LiveKit Cloud account or self-hosted server
API keys for:

Deepgram (STT)
OpenAI (LLM)
Cartesia (TTS)



Step 1: Clone the Repository
bashgit clone https://github.com/yourusername/vienna-ai-assistant.git
cd vienna-ai-assistant
Step 2: Install Dependencies
bashpip install -r requirements.txt
Required packages:
livekit-agents
livekit-plugins-deepgram
livekit-plugins-openai
livekit-plugins-cartesia
livekit-plugins-silero
python-dotenv
Step 3: Configure Environment Variables
Create a .env.local file in the project root:
bashLIVEKIT_URL=wss://your-livekit-server.com
LIVEKIT_API_KEY=your_api_key
LIVEKIT_API_SECRET=your_api_secret

DEEPGRAM_API_KEY=your_deepgram_key
OPENAI_API_KEY=your_openai_key
CARTESIA_API_KEY=your_cartesia_key
Step 4: Run the Agent
Start Vienna in console mode:
bashpython src/agent.py console
The agent will connect to your LiveKit room and start listening for voice input!

💻 Usage
Starting a Voice Session

Run the agent in console mode:

bash   python src/agent.py console

Connect to the LiveKit room using a client application or web interface
Start speaking - Vienna will respond in real-time with the cloned voice!

Voice Customization
Vienna uses a custom cloned voice (creator's own voice) for a personalized experience. You can easily customize the voice:
Option 1: Use Your Own Cloned Voice

Clone your voice using Cartesia Voice Changer
Get your custom voice ID
Update the voice parameter in src/agent.py:

python   tts=inference.TTS(
       model="cartesia/sonic-3", 
       voice="your-voice-id-here"  # Replace with your Cartesia voice ID
   )
Option 2: Use Preset Voices
Choose from Cartesia's voice library:
pythonvoice="preset-voice-id"  # e.g., "79a125e8-cd45-4c13-8a67-188112f4dd22"
Current Configuration: Vienna speaks in the creator's cloned voice (ID: abc6eacf-2626-4d87-902b-7b49c2dcae16)
Example Interactions
Medical Query:
User: "What are the symptoms of diabetes?"
Vienna: "Common symptoms include increased thirst, frequent urination, 
         unexplained weight loss, and fatigue. Would you like more details?"
Autonomous Action:
User: "Search for nearby hospitals"
Vienna: "Sure, finding nearby hospitals for you... Found several nearby 
         hospitals including City General Hospital and Care Medical Center."
Weather Check:
User: "What's the weather like in Mumbai?"
Vienna: "The weather in Mumbai is sunny, 27°C."

🔧 Configuration
Customizing the Voice
Vienna currently uses the creator's cloned voice for authentic, personalized interactions.
To use your own voice:

Visit Cartesia Voice Lab
Clone your voice (takes 2-3 minutes)
Copy your custom voice ID
Update in src/agent.py:

pythontts=inference.TTS(
    model="cartesia/sonic-3", 
    voice="your-custom-voice-id"  # Replace with your ID
)
Available Voice Options:

✅ Custom cloned voices (your own voice)
✅ Preset professional voices
✅ Multiple accent options
✅ Adjustable speaking rate and pitch

Adjusting STT Language
pythonstt=inference.STT(
    model="deepgram/nova-3-medical", 
    language="en-US"  # Change to en-US, en-GB, etc.
)
Switching LLM Models
pythonllm=inference.LLM(model="openai/gpt-4")  # Use GPT-4 for more complex reasoning

📊 Monitoring & Metrics
Vienna automatically collects and logs performance metrics:

Latency: End-to-end response time (typically < 500ms)
Token Usage: LLM token consumption and costs
Audio Quality: STT/TTS performance metrics
Tool Invocations: Function call statistics
VAD Accuracy: Voice activity detection performance

Access metrics through the UsageCollector:
pythonsummary = usage_collector.get_summary()
logger.info(f"Usage: {summary}")

🛡️ Privacy & Security

Data Privacy: All conversations are processed in real-time; no data is stored
User Confirmation: Vienna asks for confirmation before sensitive actions
Secure Communication: Uses LiveKit's encrypted WebRTC connections
API Key Safety: Environment variables for secure credential management


🤝 Contributing
Contributions are welcome! Please follow these steps:

Fork the repository
Create a feature branch (git checkout -b feature/AmazingFeature)
Commit your changes (git commit -m 'Add some AmazingFeature')
Push to the branch (git push origin feature/AmazingFeature)
Open a Pull Request


📝 API Reference
Function Tools
open_website(url: str)
Opens a specified website URL.
Parameters:

url (str): Website URL to open

Returns: Confirmation message

search_web(query: str)
Performs a web search for the given query.
Parameters:

query (str): Search query

Returns: Search initiation message

get_datetime()
Retrieves current date and time.
Returns: Formatted datetime string

lookup_weather(location: str)
Gets weather information for a location.
Parameters:

location (str): City or location name

Returns: Weather information

send_email(to: str, subject: str, body: str)
Sends an email message.
Parameters:

to (str): Recipient email
subject (str): Email subject
body (str): Email content

Returns: Confirmation message

find_nearby_places(place_type: str)
Finds nearby locations of specified type.
Parameters:

place_type (str): Type of place (restaurants, ATMs, hospitals)

Returns: List of nearby places

🐛 Troubleshooting
Common Issues
Issue: Agent not starting
bashSolution: Make sure you're in the correct directory and run:
python src/agent.py console
Issue: Agent not connecting to LiveKit
Solution: Verify LIVEKIT_URL, LIVEKIT_API_KEY, and LIVEKIT_API_SECRET in .env.local
Issue: Poor audio quality
Solution: Check internet connection and enable noise cancellation. 
Ensure you're using a good quality microphone.
Issue: STT not recognizing medical terms
Solution: Ensure you're using deepgram/nova-3-medical model, not nova-2
Issue: TurnDetector not available
Solution: The code automatically falls back to Silero VAD - this is normal and works excellently!
The VAD system is highly optimized and provides accurate voice detection.
Issue: Voice sounds different than expected
Solution: Check that you're using the correct voice ID in the TTS configuration.
Voice ID format: "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"

🗺️ Roadmap

 Add support for multiple languages (Hindi, Tamil, Bengali)
 Create voice profile library with multiple cloned voices
 Integrate electronic health records (EHR) systems
 Add appointment scheduling capabilities
 Implement medication reminders
 Create mobile app interface
 Add video consultation features
 Build symptom checker with ML models
 Improve VAD for multi-speaker scenarios
 Add emotion detection in voice


📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

👨‍💻 Author
Avijit Shil

GitHub: @yourusername
LinkedIn: www.linkedin.com/in/avijit-shil-427125332


🙏 Acknowledgments

LiveKit for the incredible real-time communication framework
Deepgram for medical-grade speech recognition
OpenAI for GPT-4.1 Mini
Cartesia for natural voice synthesis

