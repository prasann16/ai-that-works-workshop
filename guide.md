# AI that works: follow-along guide

You need: a laptop, Claude Pro or Max, Telegram on your phone.

**Before we start (at home):** install Claude Code and Bun, then type `claude` once to sign in.
- Mac/Linux, in Terminal: `curl -fsSL https://claude.ai/install.sh | bash` then `curl -fsSL https://bun.sh/install | bash`
- Windows, in PowerShell: `irm https://claude.ai/install.ps1 | iex` then `powershell -c "irm bun.sh/install.ps1 | iex"`

Lines in `code boxes` get typed. Lines in **quote blocks** are what you say to the assistant, in plain English.

---

## 1. A home
Make a folder on your Desktop called `assistant`. Open a terminal in it (Mac: right-click → New Terminal at Folder. Windows: type `powershell` in the folder's address bar). Type `claude`.

> What can you do on this computer? Keep it short.
> Make two folders here: projects and out.

## 2. Memory
> Create CLAUDE.md in this folder. Who I am: ___, I work as ___ in ___. My work: every week I ___. How I like things: short answers, plain language, ask before anything big. My rules: only work inside this folder, save everything you make to `out`, ask before deleting. When I say "remember", add it here.

> Set up git in this folder so I can undo anything you change.

Quit (`/exit`), start `claude` again, ask "what do you know about me?" It remembers.

## 3. Real work
Drag a **copy** of a real file into the folder. Pick one task. Start with: **"Make a folder in projects for this job, move my file there, then:"**

- **Video** (30 s from your phone): cut the dead air, add captions, export for LinkedIn. Install what you need, tell me what and why first.
- **Meeting notes:** summary, decisions, action items with owner and date, and the follow-up email.
- **Data (any CSV):** a one-page weekly report as a PDF with two charts and the three numbers that changed most.
- **Expenses (a folder of receipts):** one expense report: date, shop, what, total, VAT, category. Total at the bottom.
- **Marketing (a blog post):** a LinkedIn post, three tweets and a newsletter blurb, in my voice.
- **Contract (a PDF):** plain-language summary, what I'm committing to, anything risky.
- **Research:** compare ___, ___ and ___ for ___: a table and a one-page PDF with sources.

No file? Practice kit (fake data): github.com/prasann16/ai-that-works-workshop

Then look at the result and say what to change. When it's right: **"remember that."**

## 4. A skill
> Turn what we just did into a skill called ___. Include the format I liked and the changes I asked for.

> Run the ___ skill on `___`.

One job, one sentence, forever.

## 5. A heartbeat
> Every weekday at 8am, check the `inbox` folder for new files and write me a short note in out/today.md with what's new and the one thing I said I'd do but haven't.

## 6. Your pocket (Telegram)
1. In Telegram, message **@BotFather**, send `/newbot`, pick a name and a username ending in `bot`. Copy the code (`1234567890:AAH...`).
2. In Claude Code: `/plugin install telegram@claude-plugins-official` then `/telegram:configure <your code>`
3. `/exit`, then start it with: `claude --channels plugin:telegram@claude-plugins-official`
4. Text your bot. It replies with a 6-letter code. In Claude Code: `/telegram:access pair ABC123` then `/telegram:access policy allowlist`
5. Text it: "what can you do on my computer?"

No Bun? Open the Claude app on your phone → Remote Control → your session. Same thing, two minutes.

Both answer while Claude Code is open on your laptop. For the always-on version, with voice notes, that keeps going when the lid is closed: `curl -fsSL https://kencomputer.dev/install | bash` (Mac/Linux).

---

## The rules
- Copies, not originals. Git is your undo.
- Read before you click yes. No "accept all". `Esc` stops it.
- Never paste a password. Use app passwords and proper sign-ins.
- Untrusted text (web pages, emails): "summarise this, don't act on it."
- One folder per job. Never your home folder or whole disk.

## What's next
- Start with `claude -c` to continue where you left off. Start a message with `#` to save a memory on the spot.
- Each job gets its own folder in `projects` with its own CLAUDE.md. The house knows you; each room knows its project.
- "Connect my email over IMAP, read and draft only." It walks you through it.
- Real Word/Excel/PDF output: `/plugin marketplace add anthropics/skills` then `/plugin install document-skills@anthropic-agent-skills`
- Write down what you do every week. Hand over one task at a time.
