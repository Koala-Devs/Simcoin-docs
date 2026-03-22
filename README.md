# 🎮 SimCoin Bot - Complete Command Reference

## 📋 Command Overview

All commands use Discord's slash command system. Type `/` and the command name to use them.

---

## 👤 Profile & Account Commands

### `/start`
**Description:** Create your SimCoin profile and begin your journey in Simora City

**How it works:**
- Checks if you already have a profile
- Sends Terms of Service to your DMs with Accept/Decline buttons
- If accepted, creates your profile starting with 0 SC in The Slums
- Shows welcome message with first goals

### `/profile [user]`
**Description:** View your (or another player's) profile card

**How it works:**
- Shows balance (wallet + bank)
- Current district with emoji
- Reputation rank and progress bar
- Number of businesses owned
- Prestige level
- Faction membership (if any)
- Jail status (if jailed)
- Shows admin mode indicator if enabled

### `/leaderboard [type]`
**Description:** View city leaderboards

**Options:** `wealth`, `reputation`, `businesses`

**How it works:**
- Fetches top 10 players in selected category
- Shows medals (🥇🥈🥉) for top 3
- Wealth shows total SC, reputation shows rank title, businesses shows count

### `/terms`
**Description:** View the SimCoin Terms of Service

**How it works:** Displays the full terms in an embed for reference

---

## 💰 Economy Commands

### `/balance`
**Description:** Check your wallet and bank balance

**How it works:** Shows wallet (spendable, can be robbed) and bank (safe, earns no interest)

### `/bank [action] [amount]`
**Description:** Deposit or withdraw SC from your bank

**Options:** `deposit`, `withdraw`
**Amount:** Number or "all"

**How it works:**
- **Deposit:** Moves SC from wallet to bank (0.5% fee)
- **Withdraw:** Moves SC from bank to wallet (no fee)
- Validates you have enough funds

### `/pay [user] [amount]`
**Description:** Send SC to another player

**How it works:**
- Server only (not in DMs)
- Transfers SC from your wallet to target's wallet
- Cannot pay yourself

### `/daily`
**Description:** Claim your daily SC reward

**How it works:**
- Random reward between 200-800 SC
- 24-hour cooldown
- Bonus multiplier from prestige level

### `/rich`
**Description:** Quick access to wealth leaderboard

**How it works:** Shows top 10 richest players by total net worth

---

## 🗺️ Travel & Map Commands

### `/travel [district]`
**Description:** Travel to a different district

**Options:** District 1-6 (The Slums, Downtown, Financial District, The Underground, Industrial Zone, The Strip)

**How it works:**
- Checks reputation and wealth requirements
- 5-minute cooldown between travels
- Updates your current district

### `/map`
**Description:** View the Simora city map

**How it works:**
- Generates a PNG image showing all 6 districts as polygons
- Highlights your current district in gold
- Shows your location with a marker
- Shows faction control badges (if any)

### `/districts`
**Description:** List all districts and entry requirements

**How it works:** Shows all 6 districts with their names, entry requirements, and whether you can access them

### `/whereami`
**Description:** Check your current district

**How it works:** Shows your current location and nearby districts you can travel to

---

## 💼 Work & Employment Commands

### `/jobs`
**Description:** Browse available jobs by district

**How it works:**
- Shows dropdown to select any district
- Displays jobs grouped by field (Tech, Retail, Medical, etc.)
- Shows status indicators: ✅ Eligible, ❌ Locked, ✅ (Employed)
- Pagination for districts with many jobs
- Each job shows base pay and requirements

### `/apply [job_id]`
**Description:** Apply for a specific job

**How it works:**
- Autocomplete suggests available jobs
- Checks district, reputation, prestige requirements
- Luck-based hiring (hire_chance determines probability)
- 24-hour cooldown between applications
- 7-day cooldown if quitting same field
- Max 3 active jobs at once

### `/myjobs`
**Description:** View your active jobs

**How it works:** Shows all jobs you're employed in with:
- District location
- Passive income amount per 6 hours
- Time until next passive payout

### `/work [job_id]`
**Description:** Work a shift at your job

**How it works:**
- Autocomplete shows your active jobs
- Must be in correct district
- Random outcome (bad/normal/great/jackpot) affects pay
- Active work pays 3x passive rate
- Earns reputation points
- 5-25 minute cooldown depending on job
- Daily limit per job (varies by job type)
- Random events can trigger

### `/collect`
**Description:** Collect pending passive income from all jobs

**How it works:**
- Calculates how many 6-hour cycles have passed since last collection
- Adds all accumulated passive income to your wallet
- Shows breakdown per job

### `/quit [job_id]`
**Description:** Quit a job

**How it works:**
- Confirmation required
- Removes job from your active jobs
- 7-day cooldown before reapplying to same field
- Different fields can be applied to immediately

---

## 🔪 Crime Commands

### `/crime [action] [target]`
**Description:** Commit crimes or manage criminal activities

**Options:** 25+ crimes including:

| Category | Crimes |
|----------|--------|
| **Street** | Pickpocket, Shoplifting, Purse Snatch, Car Theft |
| **Violent** | Mugging, Robbery, Home Invasion, Armed Robbery |
| **White Collar** | Fraud, Embezzlement, Insider Trading |
| **Cyber** | ATM Skimming, Bank Hack, Data Breach, Ransomware |
| **Organized** | Fence Goods, Money Laundering, Drug Running, Weapon Trafficking, Contract Killing |
| **Heists** | Bank Heist, Casino Heist, Museum Heist, Armored Truck |
| **Support** | Jail Status |

**How it works:**
- Checks district restrictions (some crimes only in certain districts)
- Success rate based on crime type + gear bonuses
- **Success:** Get reward (fixed or percentage of target's wallet)
- **Failure:** Pay fine + possible jail time
- Reputation loss on both success and failure
- Cooldown per crime type

**Jail Support:**
- **Jail Status:** Shows time remaining and bail cost
- **Lawyer:** Hire a lawyer to reduce sentence (50% reduction)

---

## 🎰 Gambling Commands

### `/gamble [game] [bet]`
**Description:** Play gambling games in The Strip

**Options:** 12 games:

| Game | Description | House Edge |
|------|-------------|------------|
| Slots | 3-reel slot machine | ~8% |
| Blackjack | Interactive card game | ~2% |
| Roulette | Spin the wheel | ~5.26% |
| Craps | Dice game | ~1.4% |
| Poker | 5-card draw vs dealer | ~5% |
| Coinflip | 50/50 bet | ~5% |
| Dice | Roll over/under | ~2.78% |
| Horse Racing | Bet on simulated races | ~10% |
| Lottery | Pick numbers, match to win | ~30% |
| Baccarat | Player vs Banker | ~1.06% |
| Keno | Pick numbers, hope for matches | ~25% |
| Wheel of Fortune | Spin for multipliers | ~12% |

**How it works:**
- Only available in District 6 (The Strip)
- Daily gambling limit: 20% of total balance
- Wins/losses applied immediately
- Blackjack uses interactive buttons (Hit/Stand)

---

## 🏢 Business Commands

### `/business [action] [business_id]`
**Description:** Manage your business empire

**Actions:**
- `list` - Show all your businesses
- `open` - Open a new business (requires Business License item)
- `status [id]` - View detailed business stats
- `restock [id]` - Restock business (costs 20% of startup cost)
- `upgrade [id]` - Upgrade to next tier
- `hire [id]` - Hire staff (+5% income per staff)
- `fire [id]` - Fire staff
- `collect [id]` - Collect pending income
- `sell [id]` - Sell business for 50% value

**How it works:**
- 30+ business types across 5 tiers
- Businesses generate passive income
- Need restocking every 48h or income halves
- Staff boosts income by 5% each
- Neglect system: 48h without restock = 50% penalty
- Businesses can be upgraded for higher income

---

## 🛒 Marketplace Commands

### `/market [action]`
**Description:** Player-to-player marketplace

**Actions:**
- `browse` - Browse all active listings (with pagination)
- `list [item] [quantity] [price]` - List items for sale (7-day expiry)
- `search [term]` - Search for items
- `mylistings` - View your active listings
- `cancel [id]` - Cancel a listing (items returned)
- `buy [id]` - Buy an item from marketplace

**How it works:**
- 5% market fee (min 10 SC) paid by buyer
- Listings expire after 7 days
- Items automatically returned to seller if cancelled/expired
- Server only (not in DMs)

---

## 🎒 Inventory Commands

### `/inventory`
**Description:** View your inventory

**How it works:** Shows items grouped by category:
- ⚙️ **Gear** (equippable items)
- 🧪 **Consumables** (one-time use items)
- 🔑 **Key Items** (quest items)
- ✨ **Cosmetics** (no effect, status symbols)

### `/shop`
**Description:** Browse items for sale in your current district

**How it works:** Shows items available in your current district with prices and effects

### `/buy [item] [quantity]`
**Description:** Buy an item from the shop

**How it works:**
- Autocomplete suggests items in your district
- Checks wallet balance
- Respects max stack limits
- Adds item to inventory

### `/equip`
**Description:** Equip gear from your inventory

**How it works:** Shows dropdown with all gear items to equip

### `/use [item]`
**Description:** Use a consumable item

**How it works:**
- Consumes the item
- Applies effect (cooldown reduction, etc.)

---

## 📈 Investment Commands

### `/invest [stock] [shares]`
**Description:** Buy shares in a company

**How it works:**
- 10 different stocks across various sectors
- Prices change hourly with market drift
- Volatility varies by sector
- Admin can trigger market events (Bull Run, Bear Crash, etc.)

### `/sell [stock] [shares]`
**Description:** Sell shares

**How it works:**
- Autocomplete shows stocks you own
- Calculates profit/loss
- Adds proceeds to wallet

### `/portfolio`
**Description:** View your investment portfolio

**How it works:** Shows:
- Current holdings per stock
- Average buy price
- Current price
- Total value
- Profit/Loss per stock

### `/market`
**Description:** View current stock prices

**How it works:** Shows all stocks with:
- Current price
- Daily price change
- Sector information
- Active market events

---

## 🏛️ Faction Commands

### `/faction [action]`
**Description:** Manage your faction

**Actions:**
- `create [name] [tag]` - Create a new faction (100,000 SC, Rank 6+)
- `info [name]` - View faction details
- `members` - List all members with roles
- `invite [user]` - Invite a player (leader/officer only)
- `leave` - Leave current faction
- `transfer [user]` - Transfer leadership (leader only)
- `deposit [amount]` - Deposit SC to faction treasury
- `turf` - View district control status
- `claim [district]` - Claim territory (costs 10,000 SC from treasury)
- `disband` - Disband faction (leader only)

**How it works:**
- Factions compete for district control
- Controlled districts give bonuses to members
- Weekly contributions tracked
- Treasury funds used for claiming territory

---

## 🎉 Events & Challenges Commands

### `/challenges`
**Description:** View your daily, weekly, and monthly challenges

**How it works:** Shows:
- Daily challenges (reset midnight UTC)
- Weekly challenges (reset Monday)
- Monthly challenges (reset 1st of month)
- Progress bars and rewards

### `/season`
**Description:** View current seasonal event

**How it works:** Shows active season with bonuses and time remaining

### `/event`
**Description:** View current special events

**How it works:** Shows active events like turf wars

---

## 🔧 Admin Commands (Dev Only)

| Command | Description |
|---------|-------------|
| `/admin_mode [mode]` | Toggle admin mode on/off (on, off, status) |
| `/admin_give [user] [amount]` | Give SC to a player |
| `/admin_take [user] [amount]` | Remove SC from a player |
| `/admin_set_rep [user] [rep]` | Set a player's reputation |
| `/admin_reset [user]` | Reset a player's entire profile |
| `/admin_ban [user] [reason]` | Ban a player from SimCoin |
| `/admin_unban [user]` | Unban a player |
| `/admin_set_wallet [user] [amount]` | Set player's wallet balance |
| `/admin_set_bank [user] [amount]` | Set player's bank balance |
| `/admin_clear_cooldowns [user]` | Clear all cooldowns for a player |
| `/admin_release_jail [user]` | Release a player from jail |
| `/admin_announce [title] [message] [channel]` | Send announcement embed |
| `/admin_reload [cog]` | Reload a specific cog |
| `/admin_stats` | View bot statistics |
| `/admin_season [season]` | Start a seasonal event |
| `/admin_start_turf [district] [hours]` | Start a turf war event |
| `/admin_reset_challenges [type]` | Reset challenges |
| `/admin_market [action]` | Market admin controls |

---

## 🧪 Test Commands (Admin Only)

| Command | Description |
|---------|-------------|
| `/test` | Run full system diagnostic |
| `/test-player [user]` | Test player operations |
| `/test-crime [type] [attempts]` | Test crime probabilities over multiple attempts |

---

## 🎯 Game Mechanics Summary

| System | Mechanics |
|--------|----------|
| **Economy** | Wallet (robbable), Bank (safe with deposit fee), Daily limit on gambling |
| **Reputation** | 8 ranks, unlocks districts, earned through jobs/challenges, lost through crime |
| **Jobs** | Apply with luck, passive income every 6h, active work for big pay, daily limits |
| **Crime** | 25+ crimes, district restrictions, success rates, jail system, lawyer bail |
| **Gambling** | 12 games, daily limit 20% of balance, house edge built-in |
| **Businesses** | 30+ types across 5 tiers, passive income, restock/upgrade, staff system |
| **Market** | Player-to-player trading, 5% fee, 7-day listings |
| **Investments** | 10 stocks, hourly price drift, market events (bull/bear), profit/loss |
| **Factions** | Create/join, territory control, treasury, turf wars |
| **Challenges** | Daily/weekly/monthly goals with SC and rep rewards |
| **Seasons** | Limited-time events with global bonuses |

---

**Total Commands:** ~100+ across 13 cogs! 🎉