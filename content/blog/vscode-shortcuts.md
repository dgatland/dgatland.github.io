---
title: "My Favourite VS Code Shortcuts"
date: 2025-01-03
featured: true
description: "A collection of VS Code shortcuts that will help you become a power user of the VS Code IDE!"
tags: ["Ubuntu"]
image: ""
fact: ""
weight: 500
sitemap:
  priority : 1.0
---

I've recently learnt a bunch of shortcuts that help me to feel like more of a 'power user' of VS Code.
However, it's hard to remember them all, especially if you don't use them often or haven't needed to do certain actions 
in a while.
So, this blog post is a collection of VS Code shortcuts that I find (or think I will find) useful.

<!-- 
https://www.sitepoint.com/visual-studio-code-keyboard-shortcuts/ 
-->

### Navigating files and layout
* Ctrl+B = toggle sidebar
* Ctrl+J = toggle visibility of terminal
* Ctrl+Shift+Tab = choose to switch between open files (keep holding Ctrl to scroll through the list)
* Ctrl+P: open a file in your project (shortcut list to recent files, and you can search by filename)
* Ctrl+Shift+F: search entire project folder

### Quick code editing
* Alt+up/down = Move current line of code up or down
* F2: find and replace all references to this variable across your project (Ctrl+Enter to preview the changes)
* F3: bring up search bar (keeps the previous search test)
* Ctrl+Shift+L = Rename all occurrences of the selected text (within the file) at the same time
* Ctrl+.: while on a word with an error or warning, get suggestions to fix it

### Quick code navigation
* Ctrl+L = select current line
* Shift+up/down: extend current selection up/down a line
* Ctrl+Shift+up/down (or Ctrl+Alt+up/down): to place the cursor across rows to edit simultaneously
* Shift+Alt+drag mouse: to select blocks of text
* Ctrl+G: go to line number
* F12: go to where the selected function/class/etc. is defined
* Ctrl+Shift+F10: peek at the definition of the function/class/etc.
* Ctrl+Shift+Space: to open a popup with the functions signature (inputs and docstring) while entering inputs
* Custom shortcut: Ctrl+Shift+9: go to matching closing bracket (you can make this shortcut using Ctrl+Shift+P and click 
the settings icon next to “Go to bracket”)

### Running scripts
* F5: run current python file in debug mode
* Ctrl+F5: run current python file without debugging

### Cleaning files
* Ctrl+Shift+I: auto-format files (requires file formatter extensions to be installed, eg `ruff` for Python)

### Other
* Ctrl+,: open settings
* Ctrl+Shift+P: open command options (some of which have keyboard shortcuts)
* Ctrl+I: view function/method help while scrolling through autocomplete suggestions
