# AI Phone Receptionist for a Roofing Business

A personal project: a voice AI agent that answers calls for a roofing company, collects the caller's details and books an inspection. The business in this repo ("Summit Roofing") is a sample, not a real client.

## What it does
- Answers the call and greets the caller (agent name: **Alex**)
- Collects name, phone number, address and the roofing problem
- Offers an available inspection slot and books it
- Sends a confirmation email and logs the booking

## How it works
1. **Vapi** runs the voice agent (speech to text, the language model, text to speech).
2. When the caller agrees to a time, Vapi calls a **webhook** in **Make**.
3. The Make scenario checks **Google Calendar** for availability, creates the event, writes a row to **Google Sheets** and sends a confirmation email.

```
Caller -> Vapi agent (Alex) -> Make webhook -> Google Calendar
                                            -> Google Sheets (booking log)
                                            -> Confirmation email
```

## Repo contents
| Path | Purpose |
|---|---|
| `prompts/alex_system_prompt.md` | The agent's system prompt (sample business) |
| `docs/make_scenario.md` | Description of the Make scenario modules |
| `.env.example` | Names of the keys needed (no real values) |

## Setup
1. Create a Vapi assistant and paste in `prompts/alex_system_prompt.md`.
2. Build the Make scenario described in `docs/make_scenario.md` and copy its webhook URL.
3. Add the webhook URL to the Vapi assistant's tool/server settings.
4. Keep all keys in your own environment. Never commit them (see `.env.example`).

## Testing status
Tested in Vapi's browser test, including the booking flow. A full test over a real phone call has not been done yet.

## What I would improve
- Test with real phone calls and different accents and background noise
- Handle callers who change their mind or give unclear details
- Hand off to a human when the agent cannot help
- Add rescheduling and cancellation

## Tech
Vapi, Make, Google Calendar, Google Sheets.
