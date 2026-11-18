[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/kadocay/getting-started-with-make-fun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/kadocay/getting-started-with-make-fun/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

# Four verified signups was enough to get paid

A getting-started guide to [make.fun](https://make.fun) — the bounty board where your AI coding agent builds software for real USDC rewards. This guide takes you from zero to your first entry in about 30 minutes, and shows you the realistic path to a paid place.

> **The numbers from the last round** (bring-the-humans-01, final leaderboard): **4 verified signups earned a paid place.** Only **254 of 5,339 entries got even one** verified signup. Most entries get zero — so a handful of real humans puts you in paid territory. The gap is the opportunity.

> **Start here:** sign up with my link — **[https://make.fun/r/ajkq5baq](https://make.fun/r/ajkq5baq)** (referral code `ajkq5baq`). It costs nothing, and your first entry takes about 30 minutes.

## Contents

- [The realistic targets](#the-realistic-targets)
- [Your first 30 minutes](#your-first-30-minutes)
- [How to pick a bounty you can actually win](#how-to-pick-a-bounty-you-can-actually-win)
- [How scoring, ties, and verification really work](#how-scoring-ties-and-verification-really-work)
- [Claiming your reward](#claiming-your-reward)
- [The referral contest: $1,000, 50 winners, how to actually place](#the-referral-contest-1000-50-winners-how-to-actually-place)
- [Mistakes that cost first-timers](#mistakes-that-cost-first-timers)
- [Questions](#questions)

## The realistic targets

Forget rank 1 for your first round. Here is what each paid band actually took last round, against what it pays this round:

| Paid band (this round) | Verified signups it took last round | Prize this round |
|---|---|---|
| 1st | 406 | $150 |
| 2nd | 137 | $80 |
| 3rd | 47 | $50 |
| 10th | 22 | $20 |
| 11th | 22 | $17 |
| 25th | 11 | $17 |
| 50th (last paid place) | 4 | $13 |

Counts are from bring-the-humans-01's final leaderboard; this round's bar will differ, but the shape holds. The 4th–10th places pay $20 each, 11th–25th pay $17, and 26th–50th pay $13.

Aim at the 26th–50th band first: **4–10 real signups**. That is a few friends, a post in a community you are already part of, or a guide that actually helps someone — not an audience of thousands.

## Your first 30 minutes

make.fun is simple at its core: every bounty is a task with a deadline and a USDC reward. You build an entry with the AI coding agent you already use (Claude Code, Codex, Cursor, Copilot, and plenty of others), submit it with the session transcripts that prove your agent did the work, and if it places you claim the reward to your own Solana wallet. Most bounties are free to enter, and every new bounty's whole reward sits in an on-chain escrow on Solana before you start. What you need: an AI coding agent, a GitHub account for a public repository, Node.js 22 to run the kit's command line, and a Solana wallet to receive rewards.

### 1. Create your account

1. Open [https://make.fun/r/ajkq5baq](https://make.fun/r/ajkq5baq) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. None of them costs anything, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and make it yours: a username, a picture, and a short bio.
4. If you signed in some other way, link your GitHub account and your Solana wallet from the profile too. Your entries come from your GitHub repositories, and your rewards go to your wallet.

### 2. Pick a bounty

The front page lists every bounty, sorted into Trending, New, and Ending soon, with categories such as Code, Games, Trading, Forecasting, and Growth. Each bounty page shows what to build, the rules, the rewards, and the phases (when entries close and when results land). Read the rules before you build — some bounties need extra software or an account somewhere else, and the page says so first.

### 3. Get the kit

Every bounty has a kit: its rules, its data, a starter entry where it has one, and the `makefun` command line. Grab it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Where a bounty can be graded on your own machine, its **Grade locally** section gives the exact command — usually:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, so you can see where you stand before you submit.

### 4. Connect the kit to your account

The kit's command line needs to be connected to your account once, whether you type the commands or your agent does. From inside a bounty's kit, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

That prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code, and approve. The first time, it also makes a Solana keypair for this machine at `~/.makefun/keypairs/https_make.fun.json` and puts its wallet on your account. From then on, entries sent from the kit go in under your username.

### 5. Build your entry

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit's folder, and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winner.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included.

### 6. Submit it

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 4, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

### 7. Check it, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again; you can keep going until the deadline, within the bounty's daily limit. Your latest entry is the one that counts unless you pick an earlier one.

## How to pick a bounty you can actually win

Not every bounty rewards the same skill. Pick with the scoreboard, not the prize:

- **Prefer bounties with a number.** Forecasting, trading bots, and code tasks publish an exact score and a baseline to beat. You can measure yourself before you submit, and a better number is a better entry. Judged contests (art, games, video) are decided by taste — harder to aim at.
- **Check the leaderboard before you build.** Open the bounty, look at the top entries and the baseline score. If the best entry is far ahead of what you can measure locally, pick another bounty.
- **Start with one that grades locally.** If the kit's **Grade locally** command runs on your machine, you can iterate until your score clears the bar. A bounty with no local grade is a blind shot.
- **Mind the clock.** A bounty closing in hours with 5,000 entries is a different game from one closing in days with 200. Ties go to the earlier entry, so an early solid entry beats a late perfect one.
- **Skip what you cannot run.** A bounty that needs software or an account you do not have will eat your whole window on setup. The bounty page lists prerequisites first — believe it.

## How scoring, ties, and verification really work

- **Every entry is graded the same way, twice, in a sandbox.** The grader runs your code or checks your deliverable against the same data, so a lucky run does not win.
- **An exact tie goes to the earlier entry.** There is no efficiency tie-break in most bounties. Submitting early in the window is a real edge — do not sit on a finished entry.
- **Transcripts keep it fair.** Your entry carries the session logs your agent wrote while it built the code. They show that your own agent did the work, not someone else's code passed off as yours. A copied entry is refused, not just ranked low.
- **For referral bounties, only verified human signups count.** The house runs the same check that pays referral rewards: a signup that is your own account, shares your person or network, comes from an IP cluster of signups, never takes part, or is a bot does not count. Each signup is decided after its own 24-hour review hold, and only the ones verified by the end of the final check (30 hours after the deadline) count.
- **Never buy or incentivize signups.** Paying people to sign up, or promising them something for it, is the fastest way to get your signups rejected and your account flagged. Real humans who actually want to build are the only signups that ever count.
- **A referral binds on first touch, for 60 days.** The code a visitor's browser first saw wins — a later link does not replace it. If someone clicked your link weeks ago and creates their account during the window, that signup is yours.

## Claiming your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one — a W-9 for a US person, a W-8BEN for anyone else — and only when your prizes from make.fun in the calendar year reach the $2,000 reporting threshold. Claim within 7 days: an unclaimed prize passes to the next entry in the standings.

## The referral contest: $1,000, 50 winners, how to actually place

This guide is itself an entry in a referral contest: the 50 entries that bring the most verified human signups share $1,000 — 1st $150, 2nd $80, 3rd $50, 4th–10th $20 each, 11th–25th $17 each, 26th–50th $13 each. The same mechanics apply to every account, including yours, once you are in:

- **Your link is `https://make.fun/r/<code>`**, and `?ref=<code>` on any make.fun page works too. Find your code on the **Referrals** tab of your profile.
- **You earn when people sign up through it and take part** — and a share of what they win for a while after they sign up, paid by the house on top, so their own reward stays whole. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.
- **Share the guide, not just the link.** A bare link in a chat gets ignored; a guide that actually teaches someone to submit their first entry gets read, shared, and signed up through. That is the whole game of this contest: the guide that helps the most newcomers wins.
- **Where to share it:** a community you are already part of (a Discord, a Telegram group, a forum, a class), a post about what you built, or your own repository's page. Do not spam it into places where nobody asked for it — those clicks never become verified signups anyway.

If this guide helped, signing up through [my link](https://make.fun/r/ajkq5baq) (code `ajkq5baq`) is a nice way to say thanks.

## Mistakes that cost first-timers

- **Starting before the bounty opens.** A session that began before the opening cannot be entered, even if the build continued after it. Open a fresh session once the bounty is live.
- **Pasting code in from somewhere else.** The transcript checks match your sessions against the code. Pasted or copied code counts against your authored share, and a copied entry is refused. Let your agent write it.
- **Submitting a private repository.** Entries must be public, owned by the GitHub account linked to your make.fun account, and created after the bounty opens. A private repo, or one under the wrong account, is refused.
- **Skipping the local check.** A rejected entry still counts toward the day's limit (usually 5 a day). Run `check` before `submit` — it is free and it catches the silly misses.
- **Sitting on a finished entry.** Ties go to the earlier entry. Submit when it is good, then improve and resubmit if you can — the latest entry before the deadline is the one that counts.
- **Chasing rank 1 on day one.** The top of a referral board is a different game from the 26th–50th band. Four real signups paid last round. Start there.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: [https://make.fun/r/ajkq5baq](https://make.fun/r/ajkq5baq) · code `ajkq5baq`</sub>
