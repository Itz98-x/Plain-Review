# Plain Review

**Drop in a Lichess game and get it explained in plain English, move by move.**

Plain Review is a single-file, browser-based chess game reviewer. Load a game, and it labels every move (best, good, inaccuracy, mistake, blunder), shows what you should have played, and explains *why* in language that doesn't require being a master to understand. Everything runs locally in your browser. There is no account, no backend and nothing to install.

> Made by **98** with help from AI.

**Live demo: https://itz98-x.github.io/Plain-Review/**

---

## Features

- **Load games your way**
  - Upload a `.pgn` file
  - Paste PGN text
  - Paste a Lichess game link (it downloads the game for you)
  - Drag and drop a file onto the page
  - Try the built-in sample game
- **Move-by-move coaching** with a plain-English explanation for each move, plus tips for common beginner habits (like bringing the queen out too early)
- **Move labels:** Book, Best, Excellent, Good, Inaccuracy, Mistake and Blunder, based on how much winning chance a move gives away
- **Accuracy score** for each player, with a short verdict on the game and your weakest phase (opening, middlegame or endgame)
- **Interactive board** with:
  - Eval bar
  - Green "better move" arrow
  - Red dashed threat arrows
  - Flip board, step buttons, autoplay with adjustable speed
  - "Stop at my mistakes" option while playing
  - Keyboard controls (Left, Right, Home, End)
- **Evaluation graph:** tap or drag to jump to any move, with dots marking slips and a strip marking opening book moves
- **Key moments** list: your biggest mistakes, one tap away
- **Try a better move:** replay a mistake on the board and get instant feedback
- **Opening recognition** from a built-in opening book
- **Share and export:** copy a plain-English summary, copy or save an annotated PGN, copy the current position as FEN, open on Lichess
- **Light and dark mode**, mobile friendly layout
- Remembers which player you are (stored locally in your browser only)

## How it works

1. If your PGN already has Lichess computer analysis, Plain Review uses it straight away.
2. Otherwise it runs [Stockfish](https://github.com/nmrugg/stockfish.js) in your browser using several Web Workers side by side. Pick **Quick**, **Standard** or **Deep** depth.
3. If Stockfish can't load, it falls back to a basic built-in analysis.
4. Evaluations are converted to "winning chances" and each move is labeled by how many points it gives away.

## Usage

### Run it online
Open **https://itz98-x.github.io/Plain-Review/Plain_Review.html** in any modern browser. That's it. Nothing to install.

### Run it locally
```bash
git clone https://github.com/Itz98-x/Plain-Review.git
cd Plain-Review
# just open the file
open index.html      # macOS
xdg-open index.html  # Linux
start index.html     # Windows
```

### Getting a game from Lichess
Open a game on Lichess, then **Share & export > Download PGN**. Or just paste the game link into Plain Review.

## Requirements

- A modern browser (Chrome, Firefox, Safari, Edge)
- Internet connection on first load, since it pulls these from CDNs:
  - [chess.js](https://github.com/jhlywa/chess.js) 0.10.3 (move validation)
  - [stockfish.js](https://github.com/nmrugg/stockfish.js) 10.0.2 (engine)
  - Google Fonts (Bricolage Grotesque, IBM Plex Sans, IBM Plex Mono)
- Pasting a Lichess link requires access to `lichess.org`

## Limitations

- Standard chess only (variants like Chess960 or Crazyhouse aren't supported)
- Built for Lichess PGN exports; other PGNs usually work but aren't the focus
- Browser Stockfish is lighter than a desktop engine, so very deep analysis is slower

## Privacy

Games are analyzed entirely on your device. The only network requests are loading the libraries/fonts above and, if you paste a link, downloading that game from Lichess. Your name preference is saved in `localStorage` and never leaves your browser.

## Credits

- Made by **98** with help from AI
- Chess logic: [chess.js](https://github.com/jhlywa/chess.js)
- Engine: [Stockfish](https://stockfishchess.org/) via [stockfish.js](https://github.com/nmrugg/stockfish.js)
- Game data: [Lichess](https://lichess.org)

## License

This project is released under the [MIT License](LICENSE). Copyright (c) 2026 Itz 98.

You are free to use, copy, modify, merge, publish, distribute, sublicense and sell copies of this software, as long as the copyright notice and license text are kept. The software is provided "as is", without warranty of any kind.

Third-party libraries (chess.js, stockfish.js) are loaded from CDNs and keep their own licenses. Stockfish is GPL-licensed.
