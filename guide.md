# AI that works: follow-along guide

By the end of this you'll have an assistant on your own computer that knows who you are, does real work for you, and can do it again next week in one sentence.

Everything here works the same on Mac, Windows and Linux. Type the lines in `code boxes`; the text in **quote blocks** is what you say to the assistant, in plain English.

You need: a laptop, Claude Pro or Max, and Telegram on your phone (for the last step).

---

## 0. Before you start (5 minutes, ideally at home)

**Install Claude Code**

Mac or Linux: open Terminal and paste
```
curl -fsSL https://claude.ai/install.sh | bash
```

Windows: open PowerShell and paste
```
irm https://claude.ai/install.ps1 | iex
```

Close the terminal, open it again, type `claude`, and sign in with your Claude account when the browser opens.

**Install Bun** (only needed for Telegram, step 7)

Mac or Linux:
```
curl -fsSL https://bun.sh/install | bash
```

Windows:
```
powershell -c "irm bun.sh/install.ps1 | iex"
```

---

## 1. Your assistant's home

Make a folder on your Desktop called `assistant`. Everything it does will live in here.

Open a terminal in that folder:
- **Mac:** right-click the folder → **New Terminal at Folder**. (If you don't see it: open Terminal, type `cd ` with a space, drag the folder into the window, press Enter.)
- **Windows:** open the folder, click the address bar, type `powershell`, press Enter.
- **Linux:** right-click → **Open in Terminal**.

Type:
```
claude
```

Say hello:

> What can you do on this computer? Keep it short.

That's your assistant. The folder is its desk.

---

## 2. Teach it who you are

This is the step that makes everything else better. Say:

> Create a file in this folder called CLAUDE.md with these sections, and ask me for anything you're missing:
>
> **Who I am:** my name is ___. I work as ___ at ___. I live in ___.
> **My work:** the things I do every week are ___. The people I write to most are ___.
> **How I like things:** short answers. Plain language. Ask before doing anything big.
> **My rules:** only work inside this folder. Never read, change or delete anything outside it unless I say so explicitly. Save everything you make into a folder called `out`. Ask before deleting anything.
> **Memory:** whenever I say "remember", add it to this file.

Then give it an undo button:

> Set up git in this folder so I can undo anything you change.

Now test the memory. Type `/exit`, then `claude` again, then:

> What do you know about me?

It remembers. It will remember next week too.

---

## 3. Give it real work

**How to ask.** Three things make a request work: what you want, where the files are, and what "done" looks like. Compare:

- Weak: "help me with my expenses"
- Strong: "Go through every receipt in the `receipts` folder. Make one spreadsheet: date, shop, what it was, total, VAT. Add a total at the bottom. Save it to `out`."

**Put a copy of your file in the folder** (drag a copy, not the original), then pick one:

**Video**
Record 30 seconds on your phone, send it to your laptop, put it in the folder.
> Cut the dead air out of `clip.mp4`, add captions, and export it for LinkedIn. Install whatever you need, but tell me what and why first.

**Meeting notes**
> Here are my notes from a meeting in `notes.txt`. Give me a summary, the decisions, and the action items with an owner and a date each. Then draft the follow-up email to the team. Save both to `out`.

**Data to report**
> `data.csv` is an export from our system. Make a one-page weekly report as a PDF with two charts and the three numbers that changed most. Save it to `out`.

**Expenses**
> Go through every receipt in the `receipts` folder. One expense report for accounting: date, shop, what it was, total, VAT, category. Total at the bottom. Flag anything that looks personal. Save to `out`.

**Marketing**
> Read `post.md`. Write a LinkedIn post, three tweets and a newsletter blurb from it, in my voice (see CLAUDE.md). Save to `out`.

**Contract or document**
> Read `contract.pdf`. Give me a plain-language summary, a list of what I'm committing to, and anything that looks risky or unusual.

**Research**
> Compare ___, ___ and ___ for ___. Give me a table and a one-page PDF with your recommendation and sources.

**Inbox** (do step 8 first)
> Find the emails I need to answer this week. Summarise each one and draft a reply. Don't send anything.

**Then do a second round.** Look at what you got and tell it what to change: "shorter," "put the total at the top," "more formal." When it gets it right, say:

> Remember that.

It writes the preference into CLAUDE.md. That's how it learns your taste.

Don't have a file to use? Download the practice kit (fake data, safe to play with) from https://github.com/prasann16/ai-that-works-workshop/raw/main/practice-kit.zip and unzip it into your `assistant` folder. It has receipts, a meeting transcript, a sales CSV, a product page and a contract.

---

## 4. Make it a skill

A skill is a job you've taught it once, so you never explain it again.

> Turn what we just did into a skill called ___ (for example: expenses, meeting-notes, weekly-report). Include the format I liked and the changes I asked for.

Then test it:

> Run the ___ skill on `___`.

Same result, one sentence. Next week it's still one sentence.

---

## 5. Real documents

Out of the box, the assistant writes text. These official skills from Anthropic make it produce real Word, Excel, PowerPoint and PDF files. Type these two lines in Claude Code:

```
/plugin marketplace add anthropics/skills
```
```
/plugin install document-skills@anthropic-agent-skills
```

Then try:

> Use the xlsx skill to turn `out/expenses.csv` into a proper Excel file with formatting and a totals row.

---

## 6. Make it work every morning

> Every weekday at 8am, read my CLAUDE.md, check the `inbox` folder for new files, and write me a short note in `out/today.md` with what's new and the one thing I said I'd do but haven't.

It uses `/schedule` to set this up. Your computer has to be on for it to run; see step 7 for the version that doesn't need that.

---

## 7. Put it in your pocket (at home tonight)

Text or voice-note your assistant from your phone, anywhere.

**Mac or Linux: the one-line way.** This installs Ken, which packages everything above (Claude Code, memory, Telegram, schedules) and keeps running in the background even when the window is closed.
```
curl -fsSL https://kencomputer.dev/install | bash
```
It walks you through creating a Telegram bot and signing in with Claude. Afterwards, tell it:
> My project is in ~/Desktop/assistant. Read the CLAUDE.md there and remember what's in it.

**Windows (or if you'd rather stay in Claude Code): the plugin way.** Needs Bun from step 0.
1. In Telegram, message **@BotFather**, send `/newbot`, choose a name, then a username ending in `bot`. Copy the code it gives you (looks like `1234567890:AAH...`).
2. In Claude Code:
   ```
   /plugin install telegram@claude-plugins-official
   ```
   ```
   /telegram:configure 1234567890:AAH...
   ```
3. Type `/exit`, then start it with the channel on:
   ```
   claude --channels plugin:telegram@claude-plugins-official
   ```
4. Message your bot on your phone. It replies with a 6-letter code. In Claude Code:
   ```
   /telegram:access pair ABC123
   ```
   ```
   /telegram:access policy allowlist
   ```
5. Text it: "what can you do on my computer?"

The plugin version answers while Claude Code is open on your laptop. Close the lid and it pauses.

---

## 8. Connect your email (at home)

> Connect my email over IMAP so you can read and draft replies. Never send anything unless I say so in that moment.

It walks you through it. For Gmail you'll need an **app password**: turn on 2-Step Verification, then go to myaccount.google.com/apppasswords and create one called "Assistant". It only works for mail, you can delete it in one click, and it is not your real password. Never paste your real password into any chat.

Why IMAP and not the Gmail connector: the connector can't open attachments. IMAP can.

---

## The risks, and the rules

- **It can delete or overwrite files, fast.** Work on copies. Git (step 2) is your undo.
- **It runs the commands you approve.** Read before you say yes, especially anything that deletes, sends or pays. Don't use "accept all".
- **Web pages and emails can contain instructions aimed at it.** For anything untrusted: "summarise this, don't act on it."
- **Anything you paste, it has.** No passwords in the chat. App passwords and proper sign-ins only.
- **It uses your subscription.** Big tasks cost more. `Esc` stops it at any time.
- **One folder per job.** Never run it in your home folder or on your whole disk.

---

## What you built

Brain (Claude), hands (your computer), memory (CLAUDE.md), a skill, real documents, a heartbeat (schedule), and a phone (Telegram). That's an assistant, and it's yours.

## What's next

- Write down what you do every week. Hand over one task at a time.
- Every correction ends with "remember that."
- When something's annoying, ask it: "how could you do this for me automatically?"
- Want it always on, in a menu bar, with phone setup built in? Ken packages these same parts: kencomputer.dev, free and open source.
