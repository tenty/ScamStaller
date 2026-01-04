# Old man Voice Agent


If you're not familar with "Lenny" this was the original project that ran on a Asterix PBX and trolled scam callers.
You can view the original project at https://www.lennytroll.com/
and the Wikipedia article over at: https://en.wikipedia.org/wiki/Lenny_(bot)

To bring Lenny into the new digital age, I've now created his brother Earl which works on LiveKit and ElevenLabs and is very easy to deploy.

## Purpose

This agent is built to keep telemarketers and scammers on the line as long as possible by:

- Acting confused and forgetful
- Going on long-winded tangents about the "good old days"
- Refusing payments and requests suspiciously
- Complaining about modern technology and conspiracies

## Features

**Voice**: ElevenLabs "Bill" voice (wise, mature elderly man)
**Personality**: Earl, an 80-year-old man who loves telling stories and can never remember where he left his credit card

Requires:
- LiveKit Cloud account
- ElevenLabs API key
- All Python depdencies from LiveKit

## Technical Details

Built with LiveKit Agents framework using:
- ElevenLabs TTS for elderly male voice
- AssemblyAI for speech-to-text
- OpenAI GPT-4o-mini for reasoning
- Silero VAD for voice activity detection

## How to get started (Step By Step):
1. Sign up for a LiveKit account at: https://cloud.livekit.io/
2. Create a project, When you get prompted to create an agent, click "Create an agent with code"
3. Use the directions ot https://docs.livekit.io/deploy/agents/cloud/start/ to supercharge your repo
4. If you're using linux, grab the livekit CLI using `curl -sSL https://get.livekit.io/cli | bash` (If you're on Windows `winget install LiveKit.LiveKitCLI` or Mac: `brew install livekit-cli`)
5. Change directory into your project and type in `lk cloud auth` (this will authenticate you to your project - You'll need to make sure you're logged into LiveKit and be able to copy and paste the URL it spits out on the CLI)
6. Initialise the project with the command `uv init livekit-voice-agent --bare && cd livekit-voice-agent`
7. There are two ways to initialise the project, I built it on the STT-LLM-TTS pipeline so run these commands:
```
uv add \
  "livekit-agents[silero,turn-detector]~=1.3" \
  "livekit-plugins-noise-cancellation~=0.2" \
  "livekit-agents[elevenlabs]~=1.3" \
  "python-dotenv"

```
8. Initialise your repo with the keys: `lk app env -w`
9. Grab the necessary files: `uv run agent.py download-files`
10. Edit your .env.local file and add in an "ELEVEN_LABS_API_KEY" (there's an example in my github repo of the file `.env.local.EXAMPLE`)
11. Grab the agent.py from my repo and drop it into your local directory that you're working out of.
12. Check to make sure it's working the way you want by running the commnand `uv run agent.py dev`
13. Open up a browser and navigate to `https://agents-playground.livekit.io/` (if you don't want to use the camera go to: `https://agents-playground.livekit.io/#cam=0&mic=1&screen=1&video=1&audio=1&chat=1&theme_color=cyan` instead)
14. Click Connect and confirm that your project is working correctly. If you have to adjust any parameters, you can do so in the "agents.py" file as to how Earl sounds or reacts.
15. If you're ready to deploy to production, LiveKit can run your complete agent by typing in `lk agent create`


