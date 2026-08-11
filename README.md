# beamerthemeweiming

A clean, high-clarity Beamer template named after Wèimíng Hú (未名湖) — the "Unnamed Lake" at Peking University. Designed specifically for any presentation requiring handling of large plots, media embeds, and citations, with native support for multiple color schemes.

---

## Table of Contents

- [Overview](#overview)
- [Theme Options (Color Schemes)](#theme-options-color-schemes)
- [Acknowledgements](#acknowledgements)
- [Features](#features)
- [Installation](#installation)
- [Comprehensive TeX Example](#comprehensive-tex-example)
- [Makefile Automation](#makefile-automation)
- [Commands Reference](#commands-reference)
- [Troubleshooting](#troubleshooting)
- [License](#license)
- [Author](#author)

---

## Overview

**beamerthemeweiming** is a robust, minimalist Beamer theme developed to maximize readability and reduce visual clutter in academic presentations. 

It provides a highly consistent visual style featuring:
- Multiple high-contrast color palettes (Light, Dark, and Teal).
- Progress bars for structural pacing and section tracking.
- Dimmed red highlights to emphasize key points without inducing eye strain.
- Robust font handling that compiles flawlessly under both `pdflatex` and `xelatex`.
- Fade-in transitions for figures to mitigate sudden brightness jumps.
- Ultra-compact list environments and custom TikZ boxes for dense information display.

---

## Theme Options (Color Schemes)

The theme natively supports three distinct global color schemes to suit different environments (e.g., bright conference rooms vs. dark auditoriums). You can activate them by passing the respective option to the package:

*   **`[light]` (Default):** A high-contrast light gray/white background with dark teal text and structural elements.
    ~~~latex
    \usepackage[light]{beamerthemeweiming} % or simply \usepackage{beamerthemeweiming}
    ~~~
*   **`[dark]`:** A pure black background with white text, optimized for low-light environments and minimal eye strain.
    ~~~latex
    \usepackage[dark]{beamerthemeweiming}
    ~~~
*   **`[teal]`:** A solid dark teal background with white text, utilizing the signature Metropolis primary color across all slides.
    ~~~latex
    \usepackage[teal]{beamerthemeweiming}
    ~~~

> **Examples Provided:** To help you choose, I have added three pre-compiled PDFs alongside the `main.tex` source file: `main_light.pdf`, `main_dark.pdf`, and `main_teal.pdf`.

---

## Acknowledgements

Certain visual aesthetics, progress bar mechanics, and color palettes within this template have been heavily inspired by the excellent work found at https://github.com/matze/mtheme. Please note that this package is an independent creation built from the ground up to serve specific presentation needs, and **it is not a direct modification of that theme**.

---

## Features

| Feature | Description |
|---------|-------------|
| **Color Options** | `[light]`, `[dark]`, and `[teal]` global color schemes |
| **Progress Bars** | Automated tracking beneath frame titles and on section slides |
| **Robust Typography** | Forced Type-1 Cantarell fonts to prevent engine crashes |
| **Dimmed red highlights** | Softer red (`dimred`) for emphasis without eye strain |
| **Fade-in transitions** | 1.5-second fade for figures and embedded movies |
| **`\idea{}` and `\point{}`** | Semantic markup for main ideas and key takeaways |
| **`\plain{}`** | Bare text slides using the dark primary palette for contrast |
| **`\plotslide{}`** | Centered, full-size plot with fade-in |
| **`\plotslidecomment{}`** | Plot at top with extremely compact bullet comments below |
| **`\slidemovie{}`** | Embedded video with poster image and caption |
| **Narrow Environments** | `narrow_itemize`, `narrow_enumerate` for zero-spacing lists |
| **Custom TikZ Boxes** | Pre-styled environments like `TitleBox`, `note`, and `box` |
| **Citation Macros** | Custom gray-scaled formatting for subtle on-slide bibliographies |

---

## Installation

### Option 1: Place in Your Project Directory (Recommended)

Simply copy `beamerthemeweiming.sty` and the `Makefile` into the same folder as your `.tex` presentation file:

~~~bash
cp beamerthemeweiming.sty /path/to/your/presentation/
cp Makefile /path/to/your/presentation/
~~~

### Option 2: Install System-Wide (TeX Live)

~~~bash
# Create the directory if it doesn't exist
mkdir -p ~/texmf/tex/latex/beamerthemeweiming/

# Copy the style file
cp beamerthemeweiming.sty ~/texmf/tex/latex/beamerthemeweiming/

# Update the TeX database
texhash ~/texmf
~~~

---

## Comprehensive TeX Example

Below is a fully documented, minimal working example showcasing how to structure your presentation and utilize the custom commands provided by the `weiming` theme. Save this as `main.tex`.

~~~latex
% We recommend using the 'compress' option in Beamer to keep header elements compact.
\documentclass[10pt, compress]{beamer}

% Load our custom theme. 
% Try changing [dark] to [light] or [teal] to see the different color schemes!
\usepackage[dark]{beamerthemeweiming}

% Define your standard metadata. 
% The \maketitle command has been overridden to output this cleanly.
\title{Ancient Greek and Absurdity}
\subtitle{Aorist Cats and Dual Parrots}
\author{Pau Amaro Seoane}
\date{\today}

\begin{document}

% ---------------------------------------------------------
% 1. TITLE SLIDE
% ---------------------------------------------------------
% This will generate a clean title page devoid of headers/footers.
\maketitle

% ---------------------------------------------------------
% 2. SECTION DECLARATION
% ---------------------------------------------------------
% In this theme, \section{} silently updates the progress bar mathematics
% and the Table of Contents, but does NOT insert an automatic blank slide.
\section{The Aorist Tense and Confused Felines}

% ---------------------------------------------------------
% 3. STANDARD CONTENT FRAME
% ---------------------------------------------------------
\begin{frame}{The Punctiliar Cat}
  
  % Use \idea{} for the setup or main concept of the slide.
  \idea{The Aorist tense (from \textit{a-oristos}, "without horizon") expresses a simple, undefined action in the past.}
  
  \vspace{0.3cm}
  
  % Use narrow environments to pack information densely without wasting space.
  \begin{narrow_itemize}
    \item \grey{The Imperfect:} The cat \textit{was knocking} the vase over (ongoing).
    \item \grey{The Perfect:} The cat \textit{has knocked} the vase over (and the owner is currently angry).
    \item \grey{The Aorist:} The cat \textit{knocked} the vase over. It happened. Boom.
  \end{narrow_itemize}
  
  \vspace{0.5cm} 
  
  \idea{The Sketch Element:}
  
  \begin{narrow_itemize}
    \item A violently confused cat sits next to shattered porcelain.
    \item The cat did not "used to knock it over". It was a singular, absurd event.
  \end{narrow_itemize}

  \vspace{0.5cm}
  
  % Pair \idea{} with \point{} to drive home the slide's takeaway.
  % \point{} automatically applies the custom dimred color and italics.
  \idea{The Grammatical Reality:} \point{The Aorist cat takes no responsibility for the consequences.}
  
  % Example of using custom gray citation macros at the bottom of a slide.
  \vspace{1cm}
  \myrefs{Reference: \myREF{Smyth 1920, \S 1923} | \Citep{Ministry of Silly Felines, 1971}}
\end{frame}

% ---------------------------------------------------------
% 4. CUSTOM TIKZ BOXES
% ---------------------------------------------------------
\begin{frame}{The Aorist Passive Participle}
  \begin{center}
    \begin{tikzpicture}
      % TitleBox: A bold, orange, rounded rectangle with white text.
      \node[TitleBox] (mainbox) {The \textit{lytheis} (having-been-loosed) cat.};
      
      % note: An inverted version (white fill, orange border, black text).
      \node[note, below=0.5cm of mainbox] {A passive event completed in the past.};
    \end{tikzpicture}
  \end{center}
  
  \vspace{0.5cm}
  
  \begin{center}
    \begin{tikzpicture}
      % box: A light blue container with a red border.
      \node[box] (infobox) {
        \begin{minipage}{0.8\textwidth}
          \centering
          The Confused Cat Sketch:\\
          \vspace{0.2cm}
          "I wish to register a complaint about this feline!\\
          It is a \textit{having-been-confused} (Aorist Passive) cat!"\\
          "No sir, it's just in a state of present continuous bewilderment!"
        \end{minipage}
      };
      % fancytitle: A helper style to add a tab to the top of 'box'.
      \node[fancytitle, right=10pt] at (infobox.north west) {Dialogue Note};
    \end{tikzpicture}
  \end{center}
\end{frame}

% ---------------------------------------------------------
% 5. PLOT-ONLY FRAME
% ---------------------------------------------------------
\section{The Dual Case}

% \plotslide consumes the entire frame to display a figure. 
% It automatically applies a 1.5s fade-in transition (viewer permitting).
\plotslide{example-image.pdf}

% ---------------------------------------------------------
% 6. PLOT WITH COMMENTS FRAME
% ---------------------------------------------------------
% \plotslidecomment pushes the image up and provides space for up to 4 comments.
% The comments are formatted using the ultra-compact figcommentlist environment.
% Empty brackets at the end signify unused comment slots.
\plotslidecomment{example-image.pdf}
  {Ancient Greek features Singular, Plural, and the rare \textbf{Dual} number.}
  {The Dual is used strictly for pairs (e.g., two eyes, two hands, two parrots).}
  {Customer: "I wish to return \textit{to psittako} (these two parrots)."}
  {Shopkeeper: "They are resting! Both of them! A dual state of rest!"}

% ---------------------------------------------------------
% 7. PLAIN TRANSITION FRAME
% ---------------------------------------------------------
% \plain strips all headers, footers, and progress bars. 
% It sets the background to the dark primary color with white text, 
% regardless of the global color scheme chosen.
\plain{Part III: The Optative of Wish}

% ---------------------------------------------------------
% 8. MULTIMEDIA FRAME
% ---------------------------------------------------------
% \slidemovie embeds video content. 
% Arg 1: the video file. 
% Arg 2: a static placeholder image (poster).
% Arg 3: the caption text.
\slidemovie{example-image.pdf}{example-image.pdf}{A video of a cat wishing for a fish: "Eithe ho ichthys pareie!"}

\end{document}
~~~

---

## Makefile Automation

To ensure maximum compatibility and to automatically handle multiple compilation passes (required for Beamer progress bars and references), this theme includes a dedicated `Makefile`. 

It strictly enforces `pdflatex` compilation to prevent OpenType/TrueType system font errors.

> **Note for OpenBSD Users:** The default `make` utility on OpenBSD may not parse the provided `Makefile` correctly due to syntax differences. Please ensure you install and use GNU Make by running `gmake` instead of `make`. As an OpenBSD user, apologies...

### Usage

1. Ensure your main presentation file is named `main.tex`. (If it is named something else, edit the `PROJECT = main` line in the `Makefile`).
2. Open your terminal in the project directory and run the following commands:

*   `make` (or `gmake` on OpenBSD) — Compiles the document twice automatically, generating a perfectly synced `main.pdf`.
*   `make clean` (or `gmake clean`) — Deletes all auxiliary LaTeX clutter (`.aux`, `.log`, `.nav`, `.out`, `.snm`, `.toc`, `.vrb`).
*   `make distclean` (or `gmake distclean`) — Deletes all auxiliary files **and** the compiled `main.pdf`.

---

## Commands Reference

### 1. Semantic Markup

#### `\idea{text}`
Wraps regular content without formatting. Designed to be used alongside `\point{}` to cleanly separate a setup from its conclusion in your source code.
~~~latex
\idea{This is the main idea.} \point{This is the punchline.}
~~~

#### `\point{text}`
Highlights the key insight in **dimred italic**. Use this for the single most important takeaway on the slide.
~~~latex
\point{The degeneracy is broken instantly.}
~~~

#### `\plain{text}`
Creates a minimalist, high-contrast slide with vertically centered text. It disables headers, footers, and progress bars, applying the dark teal primary color as the background. Ideal for section breaks or powerful quotes. Note: This command retains its dark teal background even if the `[light]` or `[dark]` options are used.
~~~latex
\plain{Let's now consider the implications.}
~~~

### 2. Plots and Media

#### `\plotslide[options]{filename}`
Displays a plot scaled and centered perfectly, utilizing a 1.5-second fade-in transition to ease eye strain.
~~~latex
\plotslide{figures/violin_plots.pdf}
\plotslide[<+->]{figures/animation.pdf}  % With overlay support
~~~

#### `\plotslidecomment[options]{filename}{comment1}{comment2}{comment3}{comment4}`
Pushes a plot to the top of the slide and creates an ultra-compact list of bullet points below it. You can provide up to 4 comments; empty arguments are automatically ignored.
~~~latex
\plotslidecomment{figures/plot.pdf}{First observation}{Second}{}{}
~~~

#### `\slidemovie[options]{filename}{poster}{caption}`
Embeds a playable video. A static preview image (`poster`) is shown on the slide; clicking it begins playback.
~~~bash
# Pro-tip: Extract a poster frame using ffmpeg:
ffmpeg -i animation.mp4 -vframes 1 poster.png
~~~
~~~latex
\slidemovie{animation.mp4}{poster.png}{Simulation of an EMRI.}
~~~

### 3. List Environments

Standard LaTeX lists waste significant vertical space. Weiming includes "narrow" alternatives that reduce all item separation to exactly 1pt.

*   `\begin{narrow_itemize} ... \end{narrow_itemize}`
*   `\begin{narrow_enumerate} ... \end{narrow_enumerate}`
*   `\begin{narrow_description} ... \end{narrow_description}`

### 4. Custom TikZ Boxes

Pre-configured TikZ shapes for visually organizing text or creating callouts.

*   **`TitleBox`**: A rounded, orange box with white, centered text.
*   **`note`**: A white box with a thick orange border and black text.
*   **`box`**: A light blue box with a red border.
*   **`sectionbox`**: A borderless blue box with white text.

~~~latex
\begin{tikzpicture}
  \node[TitleBox] {Important Concept};
\end{tikzpicture}
~~~

### 5. Citation and Color Macros

A suite of commands designed to render academic citations unobtrusively.

*   **`\grey{text}` / `\verygrey{text}` / `\supergrey{text}`**: Applies varying shades of gray.
*   **`\Cite{Reference}` / `\Citep{Reference}`**: Formats a tiny, grayed-out citation block.
*   **`\myREF{Reference}`**: Formats a citation in bold, tiny orange text (useful for highlighting your own papers).
*   **`\abstractline`**: Draws a subtle, dotted gray horizontal separator.
*   **`\myrefs{Reference List}`**: Drops a tightly spaced bibliography block at the bottom of a slide, preceded by an `\abstractline`.

---

## Troubleshooting

### "Font shape undefined" or "Cantarell-Regular cannot be found"
You are likely compiling with `xelatex` on a system without Cantarell installed globally, or the font cache is outdated. 
**Solution:** Use the included `Makefile` to compile via `pdflatex`, which natively utilizes the safe Type-1 fonts bundled in this package.

### Movie doesn't play
1. **Viewer Support:** Ensure you are using **Okular** (Linux) or **Adobe Acrobat**. Standard viewers like Evince or macOS Preview often lack multimedia support.
2. **Codec Issue:** Convert your video to MP4 with the H.264 codec to maximize compatibility:
   ~~~bash
   ffmpeg -i input.mov -c:v libx264 -pix_fmt yuv420p output.mp4
   ~~~

### Progress bar doesn't advance or references show as `?`
Beamer requires multiple passes to calculate the total frame count. 
**Solution:** Run `make` (which executes `pdflatex` twice automatically).

---

## License

~~~text
Copyright (c) 2026 Pau Amaro Seoane

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
~~~

---

## Author

**Pau Amaro Seoane**  
amaro AT riseup.net
