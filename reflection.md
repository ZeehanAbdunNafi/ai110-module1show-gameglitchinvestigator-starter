# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

1. What was broken when you started?

### Bug 1: The hints were backwards
Expected:
If my guess was too high, the game should tell me to go lower. If my guess was too low, it should tell me to go higher.

Actual:
The game gave the opposite hint. A high guess showed “Go HIGHER!” and a low guess showed “Go LOWER!”, which made the feedback misleading.

Bug 2: The game instructions did not match the selected difficulty
Expected:
The range shown to the player should match the selected difficulty.

Actual:
The sidebar displayed one range based on difficulty, but the main instruction always said “Guess a number between 1 and 100.” This made the game confusing because the visible instructions were inconsistent.

Bug 3: New Game ignored the current difficulty
Expected:
Starting a new game should generate a secret number using the current difficulty range.

Actual:
Clicking New Game always reset the secret number using a range of 1 to 100, even when a different difficulty was selected.
---

## 2. How did you use AI as a teammate?

I used GitHub Copilot inside VS Code, along with ChatGPT, to help understand and debug the code. One correct suggestion Copilot made was identifying that the check_guess() function had reversed hint messages. It explained that the condition was correct but the output messages did not match, and I verified this by running the game and observing incorrect hints during gameplay. One misleading suggestion was when AI tried to overcomplicate the logic for fixing state issues by suggesting unnecessary restructuring. I verified this was incorrect by manually checking how st.session_state works and confirming that the issue was simply incorrect initialization and reset logic.

---

## 3. Debugging and testing your fixes

I decided a bug was fixed by testing both manually in the Streamlit app and automatically using pytest. For example, I ran python -m pytest to verify that the check_guess() function returned correct outcomes like "Win", "Too High", and "Too Low", and all tests passed. I also manually tested the game by playing multiple rounds to confirm that the hints and scoring behaved correctly. AI helped me understand how to structure test cases and why separating logic into logic_utils.py made testing easier. This combination of manual and automated testing gave me confidence that my fixes were correct.
---

4. What did you learn about Streamlit and state?

I learned that Streamlit reruns the entire script every time a user interacts with the app, such as clicking a button or entering input. Because of this, variables reset unless they are stored in st.session_state. Session state acts like memory for the app, allowing values like the secret number, score, and attempts to persist across reruns. Without proper use of session state, the game can behave unpredictably, such as changing the secret number or resetting progress. Understanding this helped me identify why certain bugs were happening and how to manage state correctly.
---

 5. Looking ahead: your developer habits

One habit I want to reuse is marking bugs with # FIXME comments and using focused AI prompts to debug one issue at a time. This helped me stay organized and prevented confusion when working with multiple bugs. Next time, I would be more critical of AI suggestions instead of assuming they are always correct, especially when they introduce unnecessary complexity. This project changed the way I think about AI-generated code by showing that it can produce working code that still contains logical errors. I now see AI as a helpful assistant, but one that requires careful verification and human judgment.
