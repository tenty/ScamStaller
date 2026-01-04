# Lenny Voice Agent

A voice AI agent designed to waste scammers' time by pretending to be an 80-year-old forgetful man named Lenny.

## Purpose

This agent is built to keep telemarketers and scammers on the line as long as possible by:

- Acting confused and forgetful
- Going on long-winded tangents about the "good old days"
- Refusing payments and requests suspiciously
- Complaining about modern technology and conspiracies

## Features

**Voice**: ElevenLabs "Bill" voice (wise, mature elderly man)
**Personality**: Lenny, an 80-year-old man who loves telling stories and can never remember where he left his credit card

## Usage

```bash
uv run python agent.py dev
```

Requires:
- LiveKit Cloud account
- ElevenLabs API key
- All dependencies in pyproject.toml

## Technical Details

Built with LiveKit Agents framework using:
- ElevenLabs TTS for elderly male voice
- AssemblyAI for speech-to-text
- OpenAI GPT-4o-mini for reasoning
- Silero VAD for voice activity detection