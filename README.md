# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience


 **Game's purpose**: A Streamlit-based number guessing game where players guess a secret number within a difficulty-selected range, with hints, scoring, and attempt limits.


Finding bugs: 
  - Hints were reversed (e.g., "Go HIGHER!" when guess was too high).
  - Tests failed due to `check_guess` returning tuples instead of strings.
  - "New Game" button didn't work after win/loss (due to `st.stop()` halting execution) and used wrong secret range.


 Applying fixes: 
  - Modified `check_guess` in logic_utils.py to return status strings only, aligning with tests and correct hint logic.
  - Updated "New Game" handler in app.py to reset all state (`score`, `status`, `history`) and use difficulty range (`low, high`).


## 📸 Demo

Here are some screenshots of the game in action:

![Game Screenshot 1](Screenshot%202026-03-23%20011617.png)
![Game Screenshot 2](Screenshot%202026-03-23%20011642.png)
![Game Screenshot 3](Screenshot%202026-03-23%20011710.png)
![Game Screenshot 4](Screenshot%202026-03-23%20011747.png)
![Game Screenshot 5](Screenshot%202026-03-23%20011759.png)
![Game Screenshot 6](Screenshot%202026-03-23%20011825.png)
![Game Screenshot 7](Screenshot%202026-03-23%20011841.png)


