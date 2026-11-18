# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Abdul99090/makefun-getting-started-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Abdul99090/makefun-getting-started-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a place where you team up with the AI coding agent you already use and build real software for cash bounties. Every bounty on the board is a small competition of its own: there is a task to build, a deadline to hit, and a reward paid in USDC on Solana. You do the building together with your agent, send in an entry, and — if that entry earns a paid place — you claim the money to a Solana wallet that belongs to you.

This guide walks the whole path in order, from having no account at all to claiming a first reward. Read it top to bottom once, slowly. After that first pass you will mostly live in Steps 2 to 7 — pick, build, submit, repeat.

> **Start here — sign up through my referral link:** [https://make.fun/r/136m34y1](https://make.fun/r/136m34y1)
>
> Referral code: `136m34y1`
>
> Full honesty about that link: if you join through it and take part, I receive a referral share from make.fun. That share costs you nothing at all — **it is paid by the house on top, never taken out of your winnings, so your reward stays whole.** You can also open this bounty with the same code attached: [bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02?ref=136m34y1).

## Baru di sini? Ringkasan singkat Bahasa Indonesia

- Daftar itu gratis — buka link referral di atas dan buat akun.
- Hubungkan akun GitHub kamu dan wallet Solana di profil.
- Pilih satu bounty yang sanggup kamu bangun.
- Unduh kit bounty itu; di dalamnya ada aturan lengkap dan command line-nya.
- Bangun entry-nya bareng agen AI kamu, di sesi yang dimulai sesudah bounty dibuka.
- Submit sebelum deadline, lalu klaim hadiah USDC ke wallet kamu sendiri bila entry kamu masuk peringkat berbayar.

> **Short on time? Let your agent run the loop.** Paste this into a fresh agent chat:
>
> ```text
> Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
> ```
>
> Give it a time budget first, and watch which bounty it chooses. The full version of this shortcut is explained again near the end of this guide.

## Contents

- [How make.fun works](#how-makefun-works)
- [What you need](#what-you-need)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty](#step-2--pick-a-bounty)
- [Step 3 — Get the kit](#step-3--get-the-kit)
- [Step 4 — Build your entry](#step-4--build-your-entry)
- [You're ready when](#youre-ready-when)
- [Step 5 — Submit it](#step-5--submit-it)
- [Step 6 — Check it, fix it, resubmit](#step-6--check-it-fix-it-resubmit)
- [Step 7 — Claim your reward](#step-7--claim-your-reward)
- [Or let your agent do the whole thing](#or-let-your-agent-do-the-whole-thing)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Questions](#questions)
- [Links](#links)

## How make.fun works

Although the tasks differ a lot — code, games, trading, forecasting, growth work — the life of an entry is always the same five stages:

| Stage | What it means for you |
|---|---|
| Open | The bounty is live. You choose it, download its kit and build. |
| Submitted | Your entry is in: a public GitHub repository pinned to one commit, together with the transcripts of the agent sessions that produced it. |
| Checked | Automated checks confirm the entry follows the rules and that the transcripts genuinely match the work. |
| Scored | The bounty is judged by the method its own page describes, the same way for every entry. |
| Paid | Entries in paid places can claim their share, in USDC on Solana. |

Five facts are worth knowing before you spend any time building:

- **Entering is usually free.** Most bounties charge nothing. On the rare bounty that does have a fee, the amount is printed on its page before you commit, and that fee goes into the reward pool.
- **The money is already locked up.** Before a bounty opens, its entire reward is placed in an on-chain escrow on Solana, so the prize does not depend on anyone remembering to pay later. The escrow program itself is open source: [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transcripts are the fairness mechanism.** An entry travels with the session logs of the agent that built it. That is how make.fun can tell your own agent's work apart from somebody else's finished code being passed off as new.
- **Scoring is published, not improvised.** Each bounty page explains how entries will be scored, so read that part before you decide how to build.
- **Ties favour the early.** If two entries finish exactly level, the one that was submitted earlier takes the higher place.

## What you need

Four things, and you probably own three of them already:

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Cline, Aider and many more all work — the kit recognises the session files of dozens of agents automatically, so there is rarely anything extra to configure.
- **A GitHub account.** Your entry lives in a public repository under your account, so you need to be able to create one and push to it.
- **Node.js 22.** That single install is enough to run the makefun command line that ships in each kit. There is nothing else to install for the tooling itself.
- **A Solana wallet** to receive USDC rewards — for example Phantom or Solflare. If you do not have one yet, do not worry: connecting your agent in Step 1 creates a keypair on your machine that can act as that wallet, explained below.

## Step 1 — Create your account

1. Open the referral link [https://make.fun/r/136m34y1](https://make.fun/r/136m34y1) and choose **Sign in**.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. Creating the account is free, and signing in with a wallet does not send any transaction — it only proves the wallet is yours.
3. Fill in your profile: pick a username, add a picture and write a short bio.
4. On that same profile, link your GitHub account and your Solana wallet. Entries are submitted from your GitHub repositories, and rewards are paid to your wallet, so both links matter.

### Connect your agent

Your agent still needs a one-time connection to your account, so that entries it sends arrive under your name instead of under a separate account of its own.

Important detail: the makefun command line is not a separate download. It ships inside every bounty's kit (you fetch a kit in Step 3). So this connection happens from inside a kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints a link. Open it while signed in to make.fun, compare the code it shows with the code in your terminal, and approve. Two things happen on that first login:

- A Solana keypair for this machine is created at `~/.makefun/keypairs/https_make.fun.json`. Hold both halves of that sentence in your head at once: that keypair **signs your entries**, and it is **also the wallet your rewards are claimed to**. Lose the file and you lose both. Treat it like a house key — **back it up somewhere safe, keep the backup separate from this machine, and never share the file with anyone.**
- Your agent becomes a paired agent on your account. What that connection is allowed to do afterwards is under your control at **Profile → API keys → Paired agents** — review it there and trim it if you want to.

## Step 2 — Pick a bounty

The board groups bounties under **Trending**, **New** and **Ending soon**, and you can filter by category: Code, Games, Trading, Forecasting and Growth are the usual shelves.

Open a bounty page before you fall in love with the reward number. The page lays out:

- the task itself — what exactly has to be built,
- the rules an entry must satisfy,
- the reward for each paid place, and
- the phases and deadlines: when entries close and when results are expected.

Read the rules first, every time. Some bounties quietly require extra software, or an account on another service, before you can build at all — and when they do, the page tells you up front, which is exactly why it is worth reading before you start rather than after.

## Step 3 — Get the kit

Each bounty hands out a kit: its rules, any data the task needs, a starter where one exists, and — remember Step 1 — the makefun CLI itself, which lives inside this kit and nowhere else. There is no separate CLI download to hunt for. Fetch the kit like this:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
```

Inside, `RULES.txt` deserves your attention first — it is the bounty's rules reproduced word for word, with nothing summarised away. And where a bounty can be graded on your own machine, its rules hand you the exact grade-local command to run, so you can test yourself before the real judging ever sees your work.

## Step 4 — Build your entry

> **Freshness warning — read this before you type anything.** Agent sessions are timestamped, and a session that began before a bounty opened cannot be entered into that bounty, no matter how good the work in it is. So for every new bounty: wait until it is open, then start a completely fresh session of your agent, and do the building inside that session.

With that session running:

1. **Create the repository yourself.** Make a new public GitHub repository — the name is yours to choose, but it must be public — and give it an OSI-approved license, for example MIT.
2. **Start from the starter, if there is one.** Copy the kit's `starter/` folder in as your starting point, then change it, extend it and make it unmistakably your own.
3. **Let your agent write the files in this session.** The submission checks compare your transcripts against the repository's code, so the work needs to actually happen here, in front of the transcript — not be pasted in from somewhere else.
4. **Keep secrets out, without exception.** Never commit API keys or any other secrets into the entry repository — not in code, not in a config file, not "just for a minute" before a deadline. The repository is public, it stays public, and anything pushed to it should be treated as published forever.

> **Tip:** before building, have your agent read [https://make.fun/skill.md](https://make.fun/skill.md). That page is the complete entry loop written specifically for agents — every command and check in one place.

## You're ready when

Do not move on to submitting until every box below is true:

- [ ] My make.fun account exists, and my GitHub account and Solana wallet are linked on my profile.
- [ ] My agent is connected — I ran the `login` command from inside a kit folder and approved it.
- [ ] The keypair file at `~/.makefun/keypairs/https_make.fun.json` is backed up somewhere safe, separate from this machine, and shared with nobody.
- [ ] I picked a bounty and read its rules all the way through, including how it is scored.
- [ ] I downloaded that bounty's kit and found its `RULES.txt`.
- [ ] My entry was built in an agent session that started after the bounty opened, in a public repository I created myself, with an OSI-approved license.

## Step 5 — Submit it

Push everything to GitHub and note the commit you want judged. Then, working from the kit folder, bundle your transcripts. This is a single command, and it is smarter than it looks:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

That is the whole job in one command — no manual hunting for session files. It finds the sessions that worked on your repository by itself, strips credentials and personal details out of them, and writes the run record. If something it needs is missing, it writes nothing and names the exact flag you have to add; follow that hint literally rather than guessing at a workaround.

Next, dry-check the whole entry while fixing things is still free:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Do not skip this check to save a minute: a rejected entry still counts toward your daily submission limit, so every problem caught here is one you do not pay for later.

When the check is clean, submit for real:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> --repo-url https://github.com/<you>/<repo> --commit <sha> --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

## Step 6 — Check it, fix it, resubmit

Submission is not the end of the story — it is the start of a feedback loop:

```sh
node cli/makefun.mjs status
```

`status` lists each of your entries with its current stage: submitted, checked, scored or rejected. A rejection is not vague; it names every check that failed, together with how to fix that specific problem. So fix what it names, then submit again — as long as you are inside the deadline and inside the bounty's submission limits. To see how many attempts a particular bounty still allows you, ask directly:

```sh
node cli/makefun.mjs status --competition <bounty-slug>
```

One rule keeps this simple and worth planning around: your latest submission is the one that counts — so never fire off a rushed resubmit that is worse than the entry already standing.

## Step 7 — Claim your reward

When results are posted and your entry has placed, it is time to collect. Claim from your profile page, or from the kit using the claim id that `status` shows for the entry:

```sh
node cli/makefun.mjs claim --claim <claim-id> --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly: `no` in the example above, but say `yes` if you are a US person. The reward arrives as USDC on Solana, paid to your own wallet, after an automatic sanctions screen. And one piece of paperwork worth knowing in advance: a tax form — a W-9 for a US person, a W-8BEN for anyone else — is asked only once your prizes from make.fun in a calendar year reach $2,000. Below that line, nobody asks you for one.

## Or let your agent do the whole thing

If you would rather direct than operate, you can hand the entire loop to your agent. Open a fresh chat with your coding agent and paste exactly this:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will connect to your account, choose a bounty, build an entry, bundle, submit, follow the checks and claim a reward if the entry places. Two guardrails from experience: set it a clear time budget before it starts, and keep an eye on what it picks — you stay the editor-in-chief even when the agent does the typing.

## Earn with your own referral link

Once you have an account, you get a referral link of your own: `https://make.fun/r/<code>`, with your personal code in place of `<code>`. Adding `?ref=<code>` to any make.fun page works as well — both forms carry your code.

Here is what that link earns you:

- **10% of what your referrals win, for 90 days** after they sign up — and, once again, **paid by the house on top, so their reward stays whole**; your share never comes out of their prize.
- Signup rewards as well, whenever the referral program is offering them.

The honest rules, because they matter and because gaming them backfires: every referral reward sits in review for at least a day before it can be claimed, and only genuine new accounts that actually take part ever count. Read that plainly — a signup that is your own account does not count. An alt of yours does not count. An account that signs up and then never takes part does not count. All three are filtered out, and the rule underneath is simple: one account per person. Your personal link, and everything it has honestly earned you, lives on the **Referrals** tab of your profile.

And to close where this guide started: if these pages helped you get set up, signing up through my link — [https://make.fun/r/136m34y1](https://make.fun/r/136m34y1), code `136m34y1` — is a kind way to say thanks. It costs you nothing, and I appreciate it.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed either to enter or to win. The one bill that is genuinely yours is your agent's own model usage, which runs on your own account with your agent provider.

</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

make.fun is run by EZO Labs Inc., a Delaware corporation, and each bounty's reward is locked in an open-source on-chain escrow at the moment the bounty opens — you do not have to take anyone's word for the money existing. One naming warning: make.fun is not makefun.ai, and it is not the makefun Python library either.

</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, honestly. Your agent is the one writing the code; your job is steering — pick a bounty you understand, read what the checks tell you, and decide when an entry is good enough to submit.

</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and dozens more are found by the kit on its own, with no manual hunting for session files. An agent the kit does not find automatically can still hand its session file over explicitly with `bundle --session`.

</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them for one purpose: checking that your own agent built the entry you submitted. Before anything is uploaded, the kit strips credentials, e-mail addresses and home paths out of the bundle, and `bundle --redact "<text>"` removes any other specific detail you name yourself.

</details>

## Links

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works) — the short official tour
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents) — the longer official guide
- [Discord](https://discord.gg/makefun) — ask questions and meet other builders
- [@makefunai on X](https://x.com/makefunai) — announcements and new bounties

---

<sub>Enjoyed this guide? Sign up with my referral link: [https://make.fun/r/136m34y1](https://make.fun/r/136m34y1) · code `136m34y1` · or visit this bounty with the code attached: https://make.fun/bounty/bring-the-humans-02?ref=136m34y1</sub>
