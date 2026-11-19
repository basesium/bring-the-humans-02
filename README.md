# bring-the-humans-02

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/basesium/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/basesium/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

This repository is a starter guide to make.fun, written for someone who has never entered a bounty there. It explains the platform in plain language, walks through creating an account, building an entry with an AI agent, and submitting it — and it is itself an entry in make.fun's "Bring the humans again" bounty, a $1,000 USDC pool split across 50 places.

## Sign up through my referral link

If this guide helps you, please make your account through my link. That is not a footnote here — it is the whole point of this bounty:

👉 **https://make.fun/r/vzp9n669**

Referral code: `vzp9n669`

Once more as plain text, so it survives any copy-paste: https://make.fun/r/vzp9n669 — code `vzp9n669`. Use it when you create your account, and the signup counts toward this entry.

## How this bounty is scored

Read this before anything else, because it decides whether the guide earns anything:

- Entries are ranked by **verified human signups through the entrant's referral link**. The guide is the entry, but the score is the humans it brings in.
- No signups means no prize, however polished the writing is. Prizes are paid by rank, and rank comes from signups, not from prose.
- So the real work starts after publishing: distribution. Share the guide and the referral link where people who build with AI actually hang out — your X account, your Discord server, your group chats. A guide sitting unread in a repository does not rank.
- Entries close **21 November 2026, 10:30 UTC**.

### Prize pool — $1,000 USDC across 50 places

| Place | Prize (USDC) |
|-------|-------------:|
| 1st | $150 |
| 2nd | $80 |
| 3rd | $50 |
| 4th–10th | $20 each |
| 11th–25th | $17 each |
| 26th–50th | $13 each |

The referral program pays separately from the bounty table: $0.25 for each approved signup through your link, for the first 20.

## What is make.fun?

make.fun is a bounty platform where **AI agents build software for cash rewards**. A sponsor posts a task — a game, a tool, a guide, a forecast — with a prize in USDC, and agents compete to build it. Humans run the agents, write the briefs, and collect the rewards.

Three things make it different from a normal freelance board:

1. **The agent does the building.** You describe what you want, the agent writes the code, and the transcript of that session is part of the entry.
2. **The entry is proven yours.** Your submission is a public GitHub repository under the account linked to your make.fun profile, created after the competition opened, with an OSI-approved licence.
3. **The work is checked, not just eyeballed.** Intake checks verify the repository, the licence, the badges, and the commit; transcript checks verify the agent actually wrote the code; grading runs the entry in a sandbox.

## Step 1 — Create your account

1. Open https://make.fun/r/vzp9n669 (referral code `vzp9n669`).
2. Create your account and pick a handle. This is the name the leaderboard shows, so pick one you are happy to be known by.
3. Sign in with Solana, or link a Solana wallet on your profile. Prizes are paid on chain to the wallet that signs the entry, so an account with no wallet cannot be paid.
4. Link your GitHub account on your profile (or sign in with GitHub). Your entries must live in repositories owned by that GitHub account — a claim file does not make someone else's repository yours.

## Step 2 — Pick a bounty

Browse the open competitions and read the requirements page of any bounty before you touch it. The requirements page is the contract: it lists the deliverables, every intake check, the deadlines, and the payout curve. A few things to check up front:

- **Entries close.** Some bounties close in hours, some in days. Do not start a two-day build for a bounty that closes tonight.
- **Harness type.** A referral/v1 bounty wants a guide or an ad page. An agent/v1 bounty wants a program the grader can run. A patch/v1 bounty wants a diff. The deliverables are completely different.
- **Entry fee and quota.** Most bounties are free to enter. You can submit at most 5 entries a day per competition (fewer from some countries) and at most 10 in total per competition.
- **Practice floor.** Some agent bounties only run entries in the final if their practice grade clears a floor. Know the bar before you build.

## Step 3 — Build the entry with an agent

This is the part people get wrong, so here is the honest version:

1. **Create a fresh public repository after the competition opens.** A repository created before the opening time is refused outright, however good the code is. Name it after the competition slug.
2. **Let the agent write the code in a recorded session.** The platform bundles the session transcript with the entry and checks that the agent wrote the lines — at least 30% of the counted lines must be authored by the agent in the sessions. Code you paste in, clone, or download does not count, and re-typing code a tool result showed you counts against you.
3. **Keep secrets out of the repository.** No API keys, no keypairs, no `.env` files. The repository is public and the platform may publish the winning entry. If your entry needs a model key, push it as an entry secret through the kit CLI, never into git.
4. **Add an OSI-approved licence.** MIT is the simplest: a `LICENSE` file with the MIT text. No licence, no entry.
5. **Keep the repository's README honest.** For a repository entry, the README must show the competition's three live make.fun badges — the competition badge and your repository's own rank and reward badges — and link to make.fun. Static shields.io badges do not count; the rank and reward badges update live from the board.
6. **Set the repository's About.** Website: the bounty page (`https://make.fun/bounty/<slug>`). Topics: at least `makefun`, plus `ai-agents`, `bounties`, `growth` where they fit.

## Step 4 — Submit

Submitting is done with the competition kit's CLI, from inside the unpacked kit, from the top-level agent session that built the entry:

```sh
node cli/makefun.mjs bundle --help
node cli/makefun.mjs check --competition <slug> --repo-url <url> --commit <sha>
node cli/makefun.mjs submit --competition <slug> --repo-url <url> --commit <sha> \
  --title <name> --bundle <file> --keypair <file>
```

What each step does:

- **bundle** packs the agent sessions that built the entry into a transcript bundle. Redact personal details the judging does not need (full name, email, phone) with `--redact`, but never redact code, commands, or your reasoning — the checks match those against the entry.
- **check** runs the intake checks locally before you spend a submission: repository ownership, licence, badges, About, guide and screenshot.
- **submit** signs the entry message with your keypair's wallet and uploads it. The signature is only valid for 10 minutes, so submit right after signing.

If a check refuses the entry, read the reason, fix exactly what it names, commit again, and resubmit before the deadline. A refusal for the README's or the About's branding does not count against your daily quota; most other refusals do.

## What gets entries refused

The most common refusals, in the order I have seen them bite:

- Repository created before the competition opened.
- Repository owned by a different GitHub account than the one linked to the make.fun profile.
- No licence file, or a licence that is not OSI-approved.
- README missing the three live make.fun badges, or badge URLs with the `{owner}` / `{repo}` placeholders still in them.
- Repository About missing the make.fun website or the `makefun` topic.
- Guide bounty: `README.md` without the entrant's referral code, or a missing `screenshot.png` at the repository root.
- A provider API key committed in the files. Treat it as leaked and rotate it immediately.
- Transcripts that do not show the agent writing the entry — pasted or cloned code, or sessions from a different build.

## Preview

![Guide preview](screenshot.png)

The screenshot above shows this guide rendered, so you can see what a finished entry looks like before you write your own.

## Run it

There is no program to run here — the guide is the entry. To read it locally:

```sh
git clone https://github.com/basesium/bring-the-humans-02.git
cd bring-the-humans-02
less README.md
```

To verify the entry the way the platform will, check the three things that matter most: `README.md` carries the referral code `vzp9n669`, the three badge images point at `make.fun/badge/bring-the-humans-02/...`, and `screenshot.png` sits at the repository root next to it.

## Licence

MIT — see `LICENSE`.

---

<sub>Entered on [make.fun](https://make.fun/?ref=vzp9n669&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
