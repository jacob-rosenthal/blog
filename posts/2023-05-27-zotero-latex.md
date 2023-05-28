---
author: Jacob Rosenthal
badges: false
comments: false
date: '2023-05-27'
description: Reference management for LaTeX documents
image: images/zotero-latex-post/zotero-latex-im.png
layout: post
title: Configuring Zotero and LaTeX
toc: true

---

# About

I started using [Zotero](https://www.zotero.org/) this year for reference management.
I like Zotero because it makes it easy to keep articles organized by creating hierarchical "collections" of articles.
Each collection represents a different concept (e.g., a research area, a current project, or a course I'm taking) and then I add all the relevant articles to that collection, making it really easy to go through them later. 
It also comes with browser plug-ins that let you save articles from many websites in a single click, and a Microsoft Word plug-in that lets you add references from your library while writing.
It took some initial time investment to import and organize everything, but it has definitely been worth it, and using a reference manager has been much better than my old system (i.e., downloading article pdfs into dropbox and never being able to find them again).
As a bonus, I've found the Zotero iPad app to be pretty good for reading and annotating articles.

# The Problem

Zotero unfortunately doesn't have great support for writing documents in LaTeX. I wanted keyboard shortcuts to be able to quickly copy in-text citations (e.g. `\cite{articleTag}`) and also the corresponding BibTeX entries. I also wanted to be able to control what fields were included in BibTeX entries - for example, I didn't want my `.bib` files to be bloated by including entire abstracts for each article, which seems to be the default behavior. 

# The Solution

I ended up finding a solution by combining the Zotero plug-ins [Better BibTeX (BBT)](https://retorque.re/zotero-better-bibtex/) and [Zutilo](https://github.com/wshanks/Zutilo). It took some time to figure out how to configure everything to get what I wanted, so I am documenting it here for future reference.

1. Install Better BibTeX and Zutilo plug-ins
2. Configure Better BibTeX citation preferences:
   - Under `Tools > Better BibTeX Preferences... > Export > Fields > Fields to omit from export` put `abstract,file`
3. Link Zutilo and Better BibTeX:
   - Open advanced preferences: `Zotero > Settings > Advanced > General > Config Editor`
   - Set `extensions.zutilo.quickCopy_alt1` to `export=a515a220-6fef-45ea-9842-8025dfebcc8f` (which is BBT quick copy)
   - Set `extensions.zutilo.quickCopy_alt2` to `export=ca65189f-8815-4afe-8c8b-8c7c15f0edca` (which is BBT BibTeX copy)
   - (these instructions are from [here](https://github.com/retorquere/zotero-better-bibtex/issues/2487#issuecomment-1510485367))
4. Set keyboard shortcuts:
   - Open `Tools > Zutilo Preferences... > Shortcuts`
   - Set `QuickCopy items (alt 1)` to `Command-Shift-1 (⌘ ⇧ !)`
   - Set `QuickCopy items (alt 2)` to `Command-Shift-2 (⌘ ⇧ @)`

# Result

All done! Now, the keyboard shortcuts from Zutilo are linked to the BibTeX citations export tools from Better BibTeX and can be used to quickly copy references and paste them into LaTeX documents.

- `Command-Shift-1` will copy the inline citation, e.g. `\cite{articleTag2023}`, which can be pasted into the `.tex` file. 
- `Command-Shift-2` will copy the full BibTeX citation, which can be pasted into the `.bib` file

This also works with multiple articles selected, which is pretty neat!

# In Conclusion

I hope that LLMs will finally make LaTeX obsolete, sooner rather than later. In the meantime, this is my current workflow for inserting references from Zotero into LaTeX documents on Overleaf. 
