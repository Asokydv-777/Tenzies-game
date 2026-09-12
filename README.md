# Tenzies Game

A modern implementation of the classic Tenzies dice game built with **React 19** and **Vite**. Roll ten dice until they all show the same number. Click any die to "freeze" it at its current value between rolls. The game ends when all dice are both held and showing an identical face.

![React](https://img.shields.io/badge/React-19.2.4-blue)
![Vite](https://img.shields.io/badge/Vite-8.0.0-purple)


---

## Table of Contents

- [About the Game](#about-the-game)
- [Game Rules](#game-rules)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Available Scripts](#available-scripts)
- [Project Structure](#project-structure)
- [How It Works](#how-it-works)
  - [State Management](#state-management)
  - [Core Functions](#core-functions)
  - [Components](#components)
- [Known Limitations / Future Improvements](#known-limitations--future-improvements)
- [Contributing](#contributing)
- [License](#license)

---

## About the Game

Tenzies is a fast-paced, luck-based dice game. The player starts with ten dice, each showing a random value from 1 to 6. The objective is simple: **get all ten dice to show the same number**. Between rolls, the player can click individual dice to "hold" them, preventing them from changing value on the next roll. The game is won when every die is held and all held dice display the same number.

This project was created as a learning exercise to practice React fundamentals such as state management, conditional rendering, list rendering, and event handling, while using Vite as a modern build tool.

---

## Game Rules

1. **Start** – Ten dice are rolled with random values (1–6).
2. **Roll** – Click the **ROLL** button to re-roll all dice that are *not* currently held.
3. **Hold** – Click any die to freeze its current value. A held die turns green and will not change on subsequent rolls. Click it again to release it.
4. **Win** – The game is won when all ten dice are held and all show the same number.
5. **New Game** – Once you win, the ROLL button changes to **new game**. Click it to reset the board with ten fresh dice.

---

## Features

- **Ten interactive dice** – each die is a clickable button that toggles its held state.
- **Visual feedback** – held dice are highlighted in green (`#59E391`).
- **Win detection** – the game automatically detects when all dice match and are held.
- **New game reset** – one-click restart after winning.
- **Responsive layout** – dice are arranged in a flexible container.
- **Modern tooling** – built with Vite for lightning-fast HMR and optimized production builds.

---

## Tech Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| [React](https://react.dev/) | ^19.2.4 | UI library |
| [React DOM](https://react.dev/) | ^19.2.4 | React renderer for the web |
| [Vite](https://vitejs.dev/) | ^8.0.0 | Build tool & dev server |
| [nanoid](https://github.com/ai/nanoid) | (via import) | Unique key generation for dice |
| [ESLint](https://eslint.org/) | ^9.39.4 | Linting (with React hooks & refresh plugins) |

---

## Getting Started

### Prerequisites

- **Node.js** (v18 or higher recommended)
- **npm** or **yarn** (npm is used in the examples below)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/Asokydv-777/Tenzies-game.git
   cd Tenzies-game
Install dependencies

bash
npm install
Available Scripts
Script	Description
npm run dev	Starts the Vite development server with HMR.
npm run build	Builds the production-ready bundle into the dist folder.
npm run preview	Locally previews the production build.
npm run lint	Runs ESLint across the project.
Project Structure
text
Tenzies-game/
├── public/
│   └── favicon.svg
├── src/
│   ├── assets/
│   ├── App.css          # (currently empty – styles are inline)
│   ├── App.jsx          # Main game component (logic + layout)
│   ├── Die.jsx          # Single die component
│   ├── dashboard.jsx    # Placeholder component (unused)
│   ├── index.css        # Global styles
│   └── main.jsx         # React entry point
├── .gitignore
├── eslint.config.js
├── index.html
├── package-lock.json
├── package.json
└── README.md
Note: dashboard.jsx is a placeholder and is not imported anywhere in the current codebase. App.css is also empty; all styling is handled via inline styles and index.css.

How It Works
State Management
The entire game state lives in a single useState hook inside App.jsx:

jsx
const [dice, setdice] = React.useState(() => randnum());
dice is an array of objects, each representing one die:

js
{
  value: 1–6,        // the face shown
  isHeld: false,     // whether the die is frozen
  id: nanoid()       // unique identifier for React keys
}
Core Functions
Function	Description
randnum()	Creates a fresh array of 10 random dice. Each die gets a random value (1–6), isHeld: false, and a unique nanoid.
roll()	If the game is not won, re-rolls only the dice that are not held. If the game is won, it resets the board by calling randnum().
hold(id)	Toggles the isHeld property of the die with the matching id.
Components
App.jsx – The root component. It manages state, renders the title, instructions, dice container, and the roll/new-game button. 

Die.jsx – A simple presentational component. It receives value, isHeld, and a hold callback. It renders a <button> whose background is #59E391 when held, white otherwise. Clicking the button invokes the hold callback.

Known Limitations / Future Improvements
Confetti on win – The code contains a commented-out Confetti import (// import Confetti from 'react'). Adding a confetti effect on win would be a nice enhancement.

Unused dashboard.jsx – This file can be safely removed.

Empty App.css – All styling is currently inline. Moving styles to CSS modules or a stylesheet would improve maintainability.

Prop name mismatch – App.jsx passes isheld while Die.jsx expects isHeld. This should be unified.

Accessibility – Dice buttons could benefit from aria-label or aria-pressed attributes for screen readers.

Score / timer – Adding a roll counter or timer would increase replay value.

Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page if you want to contribute.

Fork the repository.

Create a new branch (git checkout -b feature/amazing-feature).

Commit your changes (git commit -m 'Add some amazing feature').

Push to the branch (git push origin feature/amazing-feature).

Open a Pull Request.

Built with the React + Vite template.

Dice IDs generated with nanoid.

Happy rolling! 🎲
