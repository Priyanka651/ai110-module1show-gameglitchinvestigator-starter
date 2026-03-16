# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

---

## 1. What was broken when you started?

**What did the game look like the first time you ran it?**

When I first ran the game using Streamlit, the interface loaded correctly and showed the guessing game with an input box, buttons, and developer debug information. I was able to enter guesses and interact with the game, but several issues appeared while testing the gameplay.

**List at least two concrete bugs you noticed at the start.**

**Bug 1: Hint logic was incorrect**  
Expected: If my guess was lower than the secret number, the game should tell me to guess higher.  
Actual: When I entered guesses like 10, 5, and 0, the game told me “Go lower,” even though my guesses were already very small.

**Bug 2: Score behavior seemed unusual**  
Expected: The score should increase or decrease in a reasonable way during gameplay.  
Actual: The score quickly became negative, which felt strange for a guessing game.

**Bug 3: Secret number visible in debug panel**  
Expected: The secret number should be hidden from the player so the game remains challenging.  
Actual: The Developer Debug Info section showed the secret number, which made it possible to immediately win the game.

**Bug 4: Difficulty change bug**  
Expected: When switching to Easy mode, the secret number should reset within the Easy range (1–20).  
Actual: The game showed Easy mode and range 1–20, but the secret number was still something like 83, which is outside the Easy range.  
Reason: The secret number was stored in session state and did not reset when the difficulty changed.

---

## 2. How did you use AI as a teammate?

- I used AI tools such as ChatGPT and GitHub Copilot while working on this project. I mainly used AI to explain confusing parts of the code and to help understand how the game logic worked.

- One helpful suggestion from the AI was explaining that the hint logic might be reversed. This helped me understand why the hints looked incorrect during gameplay. I verified this by running the game again and comparing my guesses with the secret number shown in the debug section.

- In one case, the AI suggested a more complicated change to the code that was not necessary. Instead of applying it immediately, I reviewed the code myself and tested the game to understand the logic before making any changes.

---

## 3. Debugging and testing your fixes

- I decided a bug was fixed by running the Streamlit app again and checking whether the game behaved the way I expected.

- One manual test I performed was comparing my guesses with the secret number shown in the debug section. I confirmed that lower guesses showed “Go HIGHER” and higher guesses showed “Go LOWER.”

- I also changed the difficulty level and clicked **New Game** to verify that the secret number, attempts, score, and history reset correctly. In addition, I ran `python -m pytest`, and all three tests passed. This confirmed that the core game logic was working correctly.

- AI helped me understand what kinds of test cases to check, but I still verified the behavior myself by running the app and reviewing the test results.

---

## 4. What did you learn about Streamlit and state?

- In the original app, the secret number could become inconsistent because Streamlit reruns the script whenever the user interacts with the page. If the secret value is not managed correctly in session state, the game can behave unexpectedly when the difficulty changes.

- I would explain Streamlit reruns to a friend like this: every button click or input causes the script to run again from top to bottom. Because of this, the app must use session state to remember important values such as the secret number, score, and attempts.

- The change that finally gave the game a stable secret number was resetting the secret and related game state whenever the difficulty changed, while keeping the value stored in `st.session_state`.

---

## 5. Looking ahead: your developer habits

- One habit I want to reuse in future projects is testing small changes step by step instead of modifying too many things at once.

- This project also taught me to use AI for explanation and guidance, while still verifying everything myself by running the code and checking the results.

- Next time I work with AI on a coding task, I would ask more focused questions and avoid accepting suggestions that are more complex than the bug I am trying to fix.

- This project changed the way I think about AI-generated code because I learned that AI can be helpful, but its code still requires careful review, testing, and human judgment.
