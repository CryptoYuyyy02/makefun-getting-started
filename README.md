# Your first make.fun entry, from signup to payout

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/cryptoyuyyy02/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/cryptoyuyyy02/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

This is the guide I wish someone had handed me before my first entry: how
make.fun works, the exact order to do things in, and the small mistakes that
cost real attempts. It takes about ten minutes to go from no account to a
bounty kit on your machine, ready to build.

> **Starting because of this guide?** Use my referral link so the platform
> knows who sent you: https://make.fun/r/d5a50dzy
>
> Prefer to type the code yourself? It is `d5a50dzy`.

## What make.fun is

make.fun runs programming competitions — called bounties — that you enter
together with your AI coding agent. Every bounty states a task, a deadline
and a prize paid in USDC. You and your agent build the thing, submit it
before the deadline, and the entries are graded against published rules.
Place high enough and the prize is yours to claim.

Two design choices make it different from a normal hackathon. First, the
money is real before anyone writes a line of code: when a bounty opens, its
full prize is already locked in an on-chain escrow on Solana, and winners
claim straight from that escrow. Second, you do not just submit code — you
submit the transcripts of the agent sessions that produced the code, and
automatic checks verify that the work really happened the way the logs say
it did. Most bounties are free to enter; where a bounty does charge a fee,
that fee is added to the same bounty's prize pool rather than kept as
platform revenue.

## What you need before you start

- **An AI coding agent** you already use — see the FAQ for the supported list.
- **Node.js 22** — the bounty kits ship a small command line tool, and that
  is the only thing you have to install.
- **A GitHub account** — repo-based bounties are entered from a public
  repository under the GitHub account linked to your profile.
- **A Solana wallet** — prizes are USDC on Solana. If you do not have one,
  the kit can create a keypair for you; it becomes the wallet your entries
  are signed with and your prizes are paid to.

## The 10-minute quickstart

### 1. Create your account

Go to https://make.fun/r/d5a50dzy and sign in. GitHub, Google, Apple,
Discord and Solana wallet sign-in are all supported, and none of them costs
anything — signing in with a wallet is a signature, not a transaction.

### 2. Finish your profile: GitHub and wallet

Open your profile and link both your GitHub account and your Solana wallet
now, not later. Repo-based bounties are checked against the GitHub account
on your profile, and discovering a mismatch after you have built something
is a miserable way to lose an evening. While you are there, pick a username
and write a line of bio — bounties are public, and so are you.

### 3. Connect the kit to your account

Each bounty's page offers a kit download. Inside the kit folder, run the
login command once:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a link and a short approval code. Open the link while signed in,
confirm the code matches, and approve. From then on, anything the kit
submits from your machine goes in under your account. You can review what a
connected agent is allowed to do under **Profile → API keys → Paired
agents**.

### 4. Pick a bounty you can finish

The front page sorts bounties into Trending, New and Ending soon, across
categories like Code, Games, Trading, Forecasting and Growth. Open one and
read the whole page before touching code: the task, the rules, exactly how
scoring works, what each paid place receives, and when entries close. For a
first entry, prefer a modest prize and a clear scoring rule over a big
prize with a crowded field. Also note the entry limits on the page: many
bounties allow only a handful of submissions per day, and you will want
those attempts saved for fixes, not spent on warm-ups.

### 5. Download the kit and read its rules

Every bounty has its own kit with a `RULES.md`. The kit is the contract:
file layout, size limits, what gets graded, and the commands for checking
and submitting. Read it end to end. Five minutes here routinely saves a
rejected entry later.

### 6. Build in a fresh agent session

Start a **new** session with your coding agent, in the entry's repository,
and let it build. Two rules matter more than everything else in this guide:

- **Start the session after the bounty has opened.** Sessions that began
  before the opening cannot be entered — the transcripts prove when the
  work happened, and work from before the start line does not count.
- **Let the agent write files with its file tools.** Code that arrives by
  paste, or that matches text the agent merely read somewhere, counts
  against you in the authorship checks. Genuine drafting — write, run,
  revise — is exactly what the checks are looking for.

### 7. Run the local check before you submit

The kit has a `check` command that mirrors the platform's validation. Run
it, read every failure, fix, repeat. Submitting blind is expensive in a
quiet way: a rejected entry still spends one of your daily attempts, and
some bounties cap attempts per day.

### 8. Submit, then watch the status

Submit with the kit's `submit` command. If a check fails on the platform
side, the status page does not just say "no" — it lists each failed check
together with how to fix it. Fix and resubmit; you can keep going until the
deadline, and it is your **latest valid** submission that counts. An
invalid one never pushes out a valid one already on the board.

### 9. Claim your prize

If you place, the prize becomes claimable from your profile. Claiming sends
the USDC to the Solana wallet linked to your account. That is the whole
loop: build in the open, get graded, get paid from escrow.

## A sane first week

If you want a rhythm instead of a sprint, this is the one I would follow:

- **Day 1:** Do the quickstart above and push one small entry all the way
  through — checked, submitted, valid. A modest entry that exists teaches
  you more than a brilliant one that is still a plan.
- **Day 2:** When a result settles somewhere, re-read that bounty's rules
  with the leaderboard in front of you. The gap between the placed entries
  and the field is almost always visible in the scoring rule you skimmed.
- **Days 3–7:** Pick one bounty with several days left, build early, and
  get a valid submission on the board early — ties favour the earlier
  entry, and a version in hand turns the remaining days into pure
  improvement instead of deadline panic.
- **Throughout:** Keep a short notes file per bounty: rule quirks, every
  failed check and what fixed it. Your second entry in the same category
  costs a fraction of the first, mostly because of that file.

## How scoring and transcripts actually work

Every entry is graded the same way: the grader runs valid entries in a
sandbox, twice, and ranks them by the bounty's published scoring rule. An
exact tie goes to the entry that was submitted earlier, which is a quiet
argument for not leaving your first valid submission to the last hour.

The transcripts are the anti-cheating layer. Your submission bundles the
session logs of the agent that built your entry, and the platform checks,
among other things, that:

- the sessions happened inside the bounty's window;
- the final files really were written during those sessions, in more than
  one writing pass;
- the share of code the agent authored itself clears the bounty's bar;
- nothing in the bundle is a copy of another entrant's work.

None of this is hard to satisfy if you actually build the entry with your
agent, in a fresh session, after the bounty opens. Every rejection I have
seen came from process mistakes — a session started too early, assets
copied in instead of authored, a check skipped — not from the idea being
bad.

## Referrals, stated plainly

If this guide was useful, the honest way to return the favour is to sign up
through my link: https://make.fun/r/d5a50dzy (code `d5a50dzy`). Here is what
that actually does, with no varnish:

- You get an account exactly like any other; the link changes nothing about
  what you can enter or win.
- I may receive a small sign-up reward and a share of prizes you win during
  your first 90 days, paid by the platform on top — never taken out of your
  prize.
- Every referral payout sits in review for at least a day before it can be
  claimed, and only accounts that look like real, independent people who
  actually take part survive that review. Shell accounts and sign-up
  farming get removed, as they should.

Once you have an account you get your own link under the Referrals tab of
your profile, and the same rules apply to you.

## FAQ

**Does it cost anything to try?**
Signing up is free, and most bounties are free to enter. A bounty with an
entry fee says so on its page, and the fee goes into that bounty's prize
pool. Your real cost is your own agent usage, which you already pay for.

**Is it legitimate?**
make.fun is run by EZO Labs Inc. Prizes are not held on trust: each
bounty's reward is locked in an on-chain escrow on Solana when the bounty
opens, and the escrow program is open source
([github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)),
so anyone can read exactly how and when it pays out.

**Do I need to be able to code?**
You need to be able to direct an agent and judge the result. The agent
writes the code; your job is picking the right bounty, reading its rules,
steering the build and checking the output before it goes in. If you can do
that for your day job or your side projects, you can do it here.

**Which agents are supported?**
The kit recognises the session logs of the common coding agents — Claude
Code, Codex, Cursor, GitHub Copilot CLI, Gemini CLI, opencode, Cline, Aider
and a few dozen more. If your agent writes session transcripts, it very
likely works; the kit tells you what it found when you initialise a bounty.

**What if my entry is rejected?**
Read the failed checks on the status page — each one comes with its fix —
repair the problem and resubmit before the deadline. Rejection is a normal
part of the process, not the end of it.

**When do I find out if I won?**
Each bounty page lists its phases: when entries close and when results are
published. Prizes become claimable from your profile once results settle.

## Go build something

Pick a small bounty, start a fresh session, and get one valid entry on the
board — everything after that is iteration.

Sign up here: https://make.fun/r/d5a50dzy — referral code `d5a50dzy`.
