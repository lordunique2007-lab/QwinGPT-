# # QwinGPT

QwinGPT — by Qwin Grace 


# 🤖 Advanced AI Telegram Bot

A full-featured Telegram bot with AI chat, points system, referrals, games, admin panel, and redeem codes — all accessible via inline buttons.

---

## ✨ Features

### 👤 User Panel (inline buttons)
| Button | Description |
|--------|-------------|
| 🏆 Leaderboard | Top 10 users by points |
| 👤 Profile | Your detailed profile |
| 🤖 Switch AI | Choose AI model (GPT-4o, GPT-4o Mini, etc.) |
| ⏸ Pause | Temporarily pause your AI access |
| ▶️ Resume | Resume paused access |
| 🔗 Referral | Get your referral link |
| 💬 AI Chat | Chat with AI (requires activation) |
| 🎁 Daily Reward | Claim daily points |
| 🎟 Redeem Code | Redeem a code for points/premium |
| 📊 My Stats | Points, rank, games, referrals |
| 🎮 Play Game | Number guessing game (+1 pt per win) |
| 💎 My Plan | View Free vs Premium features |

### ⚙️ Admin Panel (inline buttons)
| Button | Description |
|--------|-------------|
| 🎟 Gen Codes | Generate redeem codes |
| ⭐ Add Premium | Grant premium to a user |
| ❌ Remove Premium | Remove premium from a user |
| 👑 Promote Admin | Make a user admin |
| 🔽 Demote Admin | Remove admin from a user |
| 👥 User Stats | Total / active / premium / banned counts |
| 📢 Broadcast | Send message to all users |
| 🏆 Global LB | Full leaderboard |
| 🔨 Ban User | Ban a user |
| ✅ Unban User | Unban a user |
| 🤖 Change AI Model | Set global default AI model |
| 🔧 Toggle Bot | Enable/disable the bot |
| 🔤 Font Style | Change global text style |
| 🎮 Game Stats | Total games and win rate |
| 🌐 Global Code | Generate a one-per-user global code |
| 👤 View User | View any user's full profile |
| 🔒 Set Mode | Toggle public / private mode |

---

## 🚀 Quick Start

### 1. Clone / download the files
```
telegram_bot/
├── bot.py
├── requirements.txt
└── .env.example
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure
Copy `.env.example` to `.env` and fill in your values:
```bash
cp .env.example .env
nano .env
```

Required values:
- `BOT_TOKEN` — from [@BotFather](https://t.me/BotFather)
- `OPENAI_API_KEY` — from [platform.openai.com](https://platform.openai.com/api-keys)
- `ADMIN_IDS` — your Telegram user ID (get it from [@userinfobot](https://t.me/userinfobot))

### 4. Run
```bash
# Load .env and run
export $(cat .env | xargs) && python bot.py

# Or set vars inline:
BOT_TOKEN=xxx OPENAI_API_KEY=xxx ADMIN_IDS=123 python bot.py
```

---

## 🎟 Redeem Code System

### Code Format
All codes start with `REF` (or `GLOBAL`) followed by 10 random characters:
```
REFaB3!xK9qW2z
GLOBALmN7@pQ1rT
```

### Generating Codes (Admin)
In the Admin Panel → **Gen Codes**, send:
```
<count> <type> <value>
```
Examples:
```
5 points 10      → 5 codes worth 10 points each
3 minutes 30     → 3 codes for 30 min of access each
2 premium 1      → 2 premium activation codes
```

### Global Codes
Admin Panel → **Global Code**: each user can redeem a global code once (not first-come-first-served).

---

## 🪙 Points System

| Action | Points |
|--------|--------|
| Referral (someone joins via your link) | +2 pts |
| Daily reward | +1 pt/day |
| Win number game | +1 pt |
| Redeem code | varies |

**Activation**: Users need **5 points** (configurable) to unlock AI chat.

---

## 🔒 Membership Gate

Set `REQUIRED_GROUPS` to require users to join channels before using the bot:
```
REQUIRED_GROUPS=@mychannel,-1001234567890
```
The bot checks membership on `/start`. Users who haven't joined see a list of required channels.

---

## 🤖 AI Models Available

| ID | Name |
|----|------|
| `gpt-4o` | GPT-4o (Best Quality) |
| `gpt-4o-mini` | GPT-4o Mini (Fast) |
| `gpt-3.5-turbo` | GPT-3.5 Turbo (Classic) |
| `claude-3-haiku` | Claude 3 Haiku (add your own API) |

---

## 📁 Database

Uses SQLite (`bot.db`). Tables:
- `users` — all user data
- `redeem_codes` — generated codes
- `global_code_redemptions` — tracks per-user global code usage
- `chat_history` — AI conversation context (last 20 messages)
- `game_stats` — all game results
- `settings` — global key-value settings

---

## 🔧 Configuration Reference

| Variable | Default | Description |
|----------|---------|-------------|
| `BOT_TOKEN` | — | Telegram bot token |
| `OPENAI_API_KEY` | — | OpenAI API key |
| `ADMIN_IDS` | `0` | Comma-separated admin user IDs |
| `REQUIRED_GROUPS` | `` | Channels users must join |
| `POINTS_TO_ACTIVATE` | `5` | Points needed to activate |
| `REFERRAL_POINTS` | `2` | Points per referral |
| `DAILY_REWARD_POINTS` | `1` | Daily check-in reward |
| `GAME_REWARD_POINTS` | `1` | Points per game win |
| `DB_PATH` | `bot.db` | SQLite database path |

---

## 📝 Commands

| Command | Description |
|---------|-------------|
| `/start` | Open main menu |
| `/admin` | Open admin panel (admins only) |
| `/stop` | Exit AI chat mode |

QwinGPT — bt Qwin Grace 
