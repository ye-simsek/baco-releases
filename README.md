# baco

A private study dashboard for IBA year 1 at RSM. It runs on your own Mac and
pulls together your Canvas deadlines, your timetable, study briefs of new
lecture decks, flashcards, and a reader for your Slim summaries with
highlighting.

Everything stays on your laptop. Your highlights, flashcard progress, grades
and briefs are yours alone; nothing is shared with anyone, including the
person who gave you baco. baco never writes or submits coursework.

## Before you start (5 minutes)

Have these three things ready:

1. **A Canvas token.** Setup opens the right Canvas page for you. There you
   click *New Access Token*, call it "baco", leave the expiry empty, and copy
   the long code it shows you.
2. **Your timetable link.** In MyTimetable choose *Connect calendar* and copy
   the iCal link.
3. **Your Slim Academy PDFs** in one folder, with a subfolder per course
   named exactly: `Intro to Business`, `Organisational Behaviour`,
   `Marketing Management`, `Mathematics`. Use your own purchased summaries;
   baco does not come with any.

For the automatic study briefs you also need a Claude subscription with
Claude Code installed (claude.com/claude-code). Without it everything else
still works.

## Install

Open **Terminal** (press Cmd+Space, type Terminal, press Enter), paste this
line, and press Enter:

    curl -fsSL https://github.com/ye-simsek/baco-releases/releases/latest/download/install.sh | sh

Then answer the questions. Press Enter to accept a suggestion, or type `s`
to skip a step; you can run `baco setup` again whenever you like.

When it finishes, close Terminal and open it again before typing any baco
command.

When it finishes, open http://127.0.0.1:8787 and bookmark it. baco keeps
itself up to date with Canvas every 30 minutes and prepares a morning brief
at 07:30.

## Everyday

| You want to | Type in Terminal |
|---|---|
| Change a setting or add something you skipped | `baco setup` |
| Get the newest version | `baco update` |
| Fetch from Canvas right now | `baco sync` |
| Read new Slim PDFs you added to the folder | `baco slim ingest` |
| See what is wrong | `baco doctor` |

If something is off, run `baco doctor` and send a screenshot of the result.
It shows no passwords or tokens.

## Good to know

- Once a day baco downloads a small public file from GitHub to see whether a
  newer version exists. Nothing about you is sent.
- Your Canvas token is a key to your Canvas account. baco stores it in the
  macOS Keychain. Never send it to anyone.
- The first time, macOS may ask whether baco may use the Keychain. Choose
  *Always Allow*.
- The summaries reader needs a small PDF tool called poppler. Setup installs
  it if you have Homebrew. If you do not, the reader shows no pages until
  you install Homebrew (brew.sh) and run `brew install poppler`, then
  `baco setup` again.

## Remove baco

    baco uninstall
    uv tool uninstall ibacopilot

The first line stops the background jobs and deletes the stored tokens. Your
data stays in the hidden folder `.ibacopilot` in your home folder; add
`--purge` to the first line to delete that too.
