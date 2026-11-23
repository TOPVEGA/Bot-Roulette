<div align="center">

# 🎲 VEGA Telegram Roulette Bot

**Create and manage Telegram channel giveaways with manual or automatic draws.**

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Telegram](https://img.shields.io/badge/Telegram-Bot-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://telegram.org/)
[![pyTelegramBotAPI](https://img.shields.io/badge/Library-pyTelegramBotAPI-2CA5E0?style=for-the-badge)](https://github.com/eternnoir/pyTelegramBotAPI)

**VEGA & Logic** · By [@TopVeGa](https://t.me/topvega)

</div>

---

## 📖 Overview

VEGA Telegram Roulette Bot is a Python Telegram bot for creating and managing giveaways (roulette draws) in Telegram channels.

Channel owners can connect channels to the bot, publish giveaway posts, choose a draw type and method, configure an optional required-subscription channel, and select the number of winners. Participants join through inline buttons, while the channel owner manages the draw.

The supplied project is implemented in a single main Python file and uses **pyTelegramBotAPI**.

## ✨ Features

### 🎯 Giveaway Creation
- Create giveaways in channels linked to the user's account.
- Choose between **Normal Roulette** and **Protected Roulette**.
- Customize the giveaway post text.
- Support Telegram HTML formatting, including bold, italic, spoiler, and blockquote tags.
- Set the required number of final winners.

### ⏱️ Draw Modes
- **Manual draw:** The creator controls when the draw begins and can proceed through participant elimination steps.
- **Automatic draw:** Set a future draw time in minutes, hours, or days.
- Automatic processing begins when the configured time is reached.
- The bot updates the giveaway post as the draw progresses.

### 🛡️ Participation Rules
- Optional conditional channel subscription before joining a giveaway.
- Global forced-subscription channels managed by the bot administrator.
- Duplicate participation checks.
- Participants can stop or resume participation where the manual-draw controls are available.
- Protected giveaways can prevent users excluded by a creator from joining that creator's future protected giveaways.

### 📢 Channel Management
- Link a channel by forwarding a message from it to the bot.
- The bot verifies that it is an administrator in the channel.
- View and remove linked channels.
- Select a linked channel when creating a giveaway.

### 👥 Participant Management
- Join a giveaway through an inline button.
- View the participant list (creator only).
- Exclude a participant (creator only).
- Receive a private notification when a participant joins a protected giveaway.
- Request a reminder if selected as a winner.

### 🧰 Administrator Panel
- View basic bot statistics.
- Add or remove global forced-subscription channels.
- Stop the bot for maintenance and enable it again.
- Restrict administrator controls to the configured administrator ID.

## 🧭 User Interface

The bot uses Telegram inline keyboards rather than a large set of text commands.

| Button / Section | Purpose |
|---|---|
| `بدء روليت` | Start creating a giveaway |
| `قنواتي` | Manage linked channels |
| `المساعدة` | Show usage instructions |
| `ذكرني إذا فزت` | Explain per-giveaway winner reminders |
| `لوحة الأدمن` | Open administrator controls (admin only) |

The `/start` command opens the main menu.

## 🧰 Requirements

- Python 3
- A Telegram bot token from [@BotFather](https://t.me/BotFather)
- The bot must be added as an administrator to each channel it manages.
- The bot needs the Telegram permissions required to publish and edit giveaway messages and check channel membership.

Python dependencies used by the source:

- `pyTelegramBotAPI` (`telebot`)
- `pytz`

Standard-library modules used include `uuid`, `re`, `random`, `threading`, `time`, and `datetime`.

## ⚙️ Configuration

The bot configuration is defined at the top of `Bot_Roulette.py`:

```python
class VegaRouletteBot:
    API_TOKEN = "YOUR_TELEGRAM_BOT_TOKEN"
    ADMIN_ID = 123456789
```

Update these values before running the application:

| Setting | Description |
|---|---|
| `API_TOKEN` | Telegram bot token received from BotFather. |
| `ADMIN_ID` | Numeric Telegram user ID allowed to access the admin panel. |

**Security:** Never publish a real bot token. If a token has been exposed, revoke it through BotFather and create a replacement. Avoid committing credentials to a public repository; environment variables or a separate private configuration file are safer.

## 🚀 Installation

### 1. Get the project

```bash
git clone YOUR_REPOSITORY_URL
cd Bot-Roulette-main
```

### 2. Install dependencies

```bash
python -m pip install -U pyTelegramBotAPI pytz
```

### 3. Configure the bot

Edit `Bot_Roulette.py` and set `API_TOKEN` and `ADMIN_ID` to your own values. Keep the token private.

### 4. Run

```bash
python Bot_Roulette.py
```

The bot starts polling Telegram for incoming updates.

## 📝 Typical Workflow

1. Send `/start` to the bot.
2. Open **My Channels** (`قنواتي`).
3. Add the bot as an administrator in your Telegram channel.
4. Forward a message from that channel to the bot to link it.
5. Choose **Start Roulette** (`بدء روليت`).
6. Select the linked channel.
7. Choose normal or protected roulette.
8. Choose manual or automatic draw.
9. Customize the giveaway message if desired.
10. Optionally add a conditional subscription channel.
11. Enter the number of winners.
12. The bot publishes the giveaway post with participation buttons.

The creator can manage participants and the draw using the controls attached to the giveaway post.

## 🗂️ Project Structure

```text
Bot-Roulette-main/
├── Bot_Roulette.py   # Main bot implementation
├── README.md         # Project documentation
└── LICENSE           # License and copyright notice
```

The supplied archive contains one main Python source file. The bot's runtime state is held in memory.

## ⚠️ Important Implementation Notes

- **No persistent database is present in the supplied source.** Linked channels, active giveaways, participants, reminders, and related state are stored in Python data structures. Restarting the process clears this runtime state.
- Automatic draw scheduling uses background threads and in-process timers. A restart can interrupt scheduled draws.
- The configured timezone for displaying automatic draw times is `Asia/Baghdad`.
- The bot's API token is a placeholder in the supplied archive and must be configured.
- The administrator ID is hard-coded in the source and should be changed before use.
- The source does not include an automated test suite.
- A channel must grant the bot sufficient administrator permissions for the requested channel operations.

## 🔐 Fairness & Responsible Use

Giveaway creators control the draw process in manual mode and can exclude participants. Make these rules clear to participants before they enter. For transparent competitions, publish eligibility requirements, draw timing, winner-selection rules, and any exclusion policy in advance.

Use the bot only in channels you own or are authorized to manage. Respect Telegram's terms, user privacy, and applicable contest and giveaway laws.

## 📄 License

The repository includes a `LICENSE` file containing an MIT-style permission notice and VEGA copyright attribution. Read the included license before copying, modifying, or redistributing the project.

## 👨‍💻 Credits

- **Project / Brand:** VEGA & Logic
- **Developer attribution in source:** [@TopVeGa](https://t.me/topvega)
- **Telegram bot library:** [pyTelegramBotAPI](https://github.com/eternnoir/pyTelegramBotAPI)
---



<!-- ═══════════════════════════════════════════════════════════════════════ --><!--                       Copyright | Footer                              --><!-- ═══════════════════════════════════════════════════════════════════════ --><div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=0:3B82F6,100:0F172A&height=4&width=40%&section=header" />
  <br><br>  <p style="color: #9CA3AF; font-size: 14px;">
    <b style="color: #3B82F6;">Brand:</b> VEGA &amp; Logic &nbsp;|&nbsp;
    <b style="color: #3B82F6;">Copyright:</b> © 2015 - 2025
  </p>
  <p style="color: #6B7280; font-size: 12px;">
  </p>
</div><br><!-- Smooth Gradient Footer Background --><img src="https://capsule-render.vercel.app/api?type=waving&color=0:3B82F6,50:1E3A8A,100:0F172A&height=120&section=footer" width="100%" /></div>
