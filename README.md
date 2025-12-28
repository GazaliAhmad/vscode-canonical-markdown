# vscode-canonical-markdown

> VS Code, but the editor keeps its opinions to itself.

This repository exists because at some point I realized I was spending more time arguing with my editor than reading my own files.

## Markdown

I work with large Markdown files. Hundreds, sometimes thousands of lines. They are not essays. They are not blog posts. They are canonical text, source material, and inputs to other systems. They are written intentionally.

Modern editors assume Markdown is prose.
This repository assumes Markdown is data.
That difference explains everything here.

At some point VS Code decided that when scrolling through a long file, it should helpfully pin a few lines at the top of the screen. Not lines I chose. Not lines I care about. Just whatever it thinks is “context”.

### Sticky Scroll

Sticky Scroll is fine until you are halfway through a thousand-line file checking references and the editor insists on showing headings that have nothing to do with what you are looking at. It changes dynamically as you scroll. It steals vertical space. It creates motion where there should be stability.

If I want fixed context, I split the editor. That pattern has existed forever. It is explicit, predictable, and does not guess.

**So Sticky Scroll is off.**

### MD Linting
Markdown linting follows the same pattern.

If I start a file with:

```
## Scope
```

instead of:

```
# Title
```

nothing breaks.

The Markdown renderer is fine.
GitHub is fine.
Every downstream tool is fine.

The only thing complaining is a linter enforcing a publishing convention that does not apply here.

These files are not books. They do not require ceremonial structure. Headings mean what I say they mean.

**So markdownlint is off.**

---

## Spellchecker
Then there is the spell checker.

At some point it flagged `jekyll`.

A proper noun.
A well-known tool.
A real dependency.

The suggested fix was to add it to an exceptions list.

No.

If a tool cannot distinguish domain language from a spelling mistake, the solution is not to keep teaching it vocabulary one word at a time. That is an endless and losing game. The correct response is to remove its authority entirely.

**So spell checking is off.**

This repository contains a VS Code **workspace-level configuration** that disables:

* spell checking (all variants)
* Markdown validation
* Markdown linting
* auto-formatting and format-on-save
* sticky scroll (editor and terminal)
* hover hints and semantic highlighting
* word-based suggestions
* Unicode “suspicious character” warnings

The goal is simple.

Two developers open the same repository and see the same reality.
No yellow or red squiggles arguing about intent.
No editor “helpfulness” leaking into meaning.
No hidden state causing peer confusion.

**The editor becomes what it should have been all along: a surface.**

## Usage

To use this configuration, create a folder named `.vscode` at the root of your repository. Inside that folder, place a file named [`settings.json`](settings.json). Copy the [`settings.json`](settings.json) from this repository into that location.


This configuration must live at the workspace level. VS Code applies language services and diagnostics per workspace. User-level settings are advisory. Workspace settings are authoritative. That is why the `.vscode` folder is committed to Git.

---

## This is not personal preference.
**It is policy.**

The recommended way to work with large files under this setup is to use split editors for fixed context instead of dynamic UI features. Treat headings as semantic markers, not formatting rules. Read deliberately. Scroll intentionally. Let tools obey, not supervise.

If you prefer an assistive, opinionated editing experience, this setup will feel hostile. That is fine. This repository is not trying to be universal.

It is trying to be honest.

The license is MIT. Do what you want.

Just don’t tell me my headings are wrong. 

Linting & SpellChecker Police Department (LSPD) have **no jurisdiction**  here.
