# Grok Wake

Say "hey research" and Grok Wake starts a voice chat with your Research bot in Grok Bot. It sits in the menu bar, listens for the phrases you set (one per bot), and when it hears one it opens that bot and presses its "Start voice chat" button for you.

Speech recognition runs on your Mac. No audio or text goes over the network, and Grok Wake stops listening while a call is going.

## Requirements

- macOS 13 (Ventura) or later, Apple silicon or Intel.
- Grok Bot, signed in, with at least one bot.
- On-device speech recognition for English (US). macOS downloads it when Dictation is on: System Settings > Keyboard > Dictation. You can turn Dictation off again afterwards; the download stays.

## Install

1. Download [**Grok-Wake.zip**](https://github.com/ExpeditedProjects/grokbot-wakeword-releases/releases/latest/download/Grok-Wake.zip) and double-click it to unzip.
2. Drag **Grok Wake** to your Applications folder.
3. Open it. If macOS asks whether to open an app downloaded from the internet, click **Open**.

Grok Wake appears in the menu bar, not the Dock. Keep it in Applications before turning on Launch at Login, so the login item points at the copy you keep.

## Update

Quit Grok Wake (menu > Quit), download the latest release, and replace the copy in Applications. Your phrases and permissions are kept.

## First run

Grok Wake starts with Listening off. Click its icon in the menu bar and turn **Listening** on. macOS then asks for:

1. **Microphone**, to hear your wake phrases.
2. **Speech Recognition**, to turn what it hears into text on your Mac.

It also needs **Accessibility**, to press Grok Bot's voice button. Click **Accessibility: Allow…** in the menu, then turn Grok Wake on in System Settings > Privacy & Security > Accessibility.

If you said no to a prompt, the menu shows a button that opens the right System Settings pane.

## Phrases

Open **Settings…** from the menu to see your bots. Each one has:

- a checkbox to turn its phrase on or off (all are on at first), and
- a phrase, which starts as "hey" plus the bot's name ("hey research" for Research). Type a new one to change it; clear the field to go back to the default.

Matching ignores case and punctuation and works on whole words, so "Hey, Research!" wakes Research but "hey researcher" doesn't. The phrase can come anywhere in what you say ("uh, hey research, what's up"). When the phrase is the last thing you said, Grok Wake waits about half a second to be sure you weren't in the middle of a longer word.

If two bots have the same phrase, Settings marks them with a warning and the one higher in the list wins. If one phrase starts another ("hey crux" and "hey crux two"), the longer one wins when you say it.

Bot names that speech recognition spells oddly (made-up words, brackets, initials) work better with a phrase in plain words. The **Heard** line at the bottom of Settings shows what Grok Wake last heard, which helps you pick a phrase it recognizes.

## The menu bar icon

| Icon | Meaning |
|---|---|
| Waveform | Listening |
| Pause | Listening is off |
| Phone | A call is starting or in progress (not listening) |
| Warning | Something needs attention; open the menu to see what |

## Privacy

- Recognition is on-device only. Grok Wake requires it and never falls back to Apple's servers. If on-device recognition isn't available, it shows an error instead of listening.
- Grok Wake makes no network connections. It reads your bot list from Grok Bot's files on your Mac.
- What it hears is kept only long enough to check for a phrase. Recognition restarts about every 50 seconds and after every wake, which discards the old text. Nothing is saved to disk.
- While a call is starting or live, Grok Wake turns the microphone off completely, so it can't hear your conversation. macOS's orange microphone dot then belongs to Grok Bot alone, and Bluetooth headsets go back to high-quality audio after the call. This includes calls you start yourself in Grok Bot.
- When Listening is on, macOS shows the orange microphone dot in the menu bar. That's expected: Grok Wake has to hear you to catch the phrase.

## Troubleshooting

**"On-device speech recognition isn't available."** Turn on Dictation (System Settings > Keyboard), wait for the download, then turn Listening off and on.

**It never wakes.** Open Settings and watch the Heard line while you speak. If nothing appears, check the microphone permission and the input device in System Settings > Sound. If the words come out differently from your phrase, change the phrase to match.

**It hears the phrase but nothing happens in Grok Bot.** Check that Accessibility is allowed in the menu. If the menu shows "Couldn't find the Start voice chat button", clear any text in that bot's message box: Grok Bot hides the voice button while there's a draft.

**The permissions stopped working.** Remove Grok Wake from the list in System Settings > Privacy & Security (Microphone, Speech Recognition, Accessibility), then allow it again from the menu.

**Check a phrase without speaking.**

```sh
"/Applications/Grok Wake.app/Contents/MacOS/grok-wake" --match "uh hey research what's up"
```

It prints which bot that sentence would wake with your current settings.

## Problems and requests

[Open an issue](https://github.com/ExpeditedProjects/grokbot-wakeword-releases/issues). Include your macOS version, Grok Wake version (bottom of the Settings window) and what the menu says.

## License

MIT. See [LICENSE](LICENSE).
