# AI that works: build your assistant

## 0. Install
Go to **claude.com/code**. Copy the install command for your computer, paste it in your terminal (Mac: Terminal · Windows: PowerShell), press Enter. Then type `claude` and sign in.

## 1. A home
Folder on your Desktop called `assistant`. Open a terminal there. Type `claude`.
> What can you do on this computer?
> Make two folders here: projects and out.

## 2. Memory
> Create CLAUDE.md in this folder. Who I am: ___. My work: every week I ___. How I like things: short answers, plain language, ask before anything big. Rules: only work inside this folder, save what you make to `out`, ask before deleting. When I say "remember", add it here.

Quit (`/exit`), start `claude` again, ask what it knows about you.

## 3. Real work
Drag a **copy** of a real file in. Pick one. Say: **"Make a folder in projects for this job, move my file there, then:"**

- **Video** (30 s from your phone): cut the dead air, add captions, export for LinkedIn.
- **Meeting notes:** summary, decisions, action items with owner and date, follow-up email.
- **Any CSV:** one-page weekly report as a PDF, two charts, the three numbers that changed most.
- **Receipts:** one expense report: date, shop, what, total, VAT. Total at the bottom.
- **Blog post:** a LinkedIn post, three tweets and a newsletter blurb, in my voice.
- **Contract PDF:** plain-language summary, what I'm committing to, anything risky.
- **Research:** compare ___, ___ and ___: a table and a one-page PDF with sources.
- **Website:** build me a one-page personal website from my CLAUDE.md and open it in my browser.

Say what to change. When it's right: **"remember that."** No file? Practice kit: github.com/prasann16/ai-that-works-workshop

## 4. A skill
> Turn what we just did into a skill called ___.
> Run the ___ skill on `___`.

## 5. A heartbeat
> Every weekday at 8am, write me a note in out/today.md with what's new and the one thing I said I'd do.

## 6. Your pocket
Telegram → @BotFather → `/newbot` → copy the code. Then in Claude Code:
`/plugin install telegram@claude-plugins-official` · `/telegram:configure <code>` · restart with `claude --channels plugin:telegram@claude-plugins-official` · text your bot, pair with `/telegram:access pair <6 letters>`.
(Needs Bun, from **bun.sh**. No Bun? Claude app → Remote Control.)

Always-on, lid closed, voice notes: `curl -fsSL https://kencomputer.dev/install | bash`

**Rules:** copies not originals · read before you click yes · never paste a password · one folder per job · `Esc` stops it.
