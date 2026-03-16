  # 💭 Reflection: Game Glitch Investigator

  Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

  ## 1. What was broken when you started?

  - What did the game look like the first time you ran it?
  - List at least two concrete bugs you noticed at the start  
    (for example: "the secret number kept changing" or "the hints were backwards").

  ---
When I first ran the game using Streamlit, the interface loaded correctly and I could see the guessing game with the input box, buttons, and developer debug information. I was able to enter guesses and play the game, but I noticed several issues while testing it.

Bug 1: The hint messages seemed incorrect.  
Expected: If my guess was lower than the secret number, the game should tell me to guess higher.  
Actual: When I entered guesses like 10, 5, and 0, the game kept telling me “Go lower,” even though my guesses were already very small.

Bug 2: The score behavior seemed unusual.  
Expected: The score should increase or decrease in a reasonable way during gameplay.  
Actual: The score quickly became negative, which felt strange for a guessing game.

Bug 3: The secret number was visible in the Developer Debug Info section.  
Expected: The secret number should be hidden from the player so the game remains challenging.  
Actual: The debug section shows the secret number, which makes it possible to immediately win the game by entering that number.

Bug 4: Difficulty change bug
Expected: When I change the difficulty to Easy, the secret number should also reset within the Easy range (1 to 20).
Actual: The game showed Easy mode and range 1 to 20, but the secret number was still 83, which is outside the Easy range.
Reason: The secret number was stored in session state and did not reset when the difficulty changed.
Fix idea: Reset the secret, attempts, score, status, and history when the difficulty changes.

  ## 2. How did you use AI as a teammate?

  - Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  - Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  - Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

  ---
I used AI tools- ChatGPT and GitHub Copilot while working on this project. I asked AI to explain parts of the code that were confusing, especially the check_guess function and how the hint system worked.

One helpful suggestion from the AI was explaining that the hint logic might be reversed, which helped me understand why the hints looked incorrect during gameplay. I verified this by running the game again and comparing my guesses with the secret number shown in the debug section.

In one case, the AI suggested a more complex change to the code that did not seem necessary. Instead of applying it immediately, I reviewed the code myself and tested the game to better understand the logic before making any changes.
-----
## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?
---
I decided a bug was fixed by running the Streamlit app again and checking whether the game behaved the way I expected. 

I manually tested the hint system by comparing my guesses with the secret number shown in the debug section, and I confirmed that lower guesses showed “Go HIGHER” and higher guesses showed “Go LOWER.” I also changed the difficulty and clicked New Game to make sure the secret number, attempts, score, and history reset correctly. In addition, I ran `python -m pytest`, and all 3 tests passed, which confirmed that the core game logic was working correctly. 

AI helped me understand what kinds of test cases to check, but I still verified the behavior myself in both the app and the test results.

------

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?
---
In the original app, the secret number could become inconsistent because Streamlit reruns the script whenever the user interacts with the page. If the secret value is not managed carefully in session state, the game can keep old values or behave unexpectedly when the difficulty changes. 

I would explain Streamlit reruns to a friend like this: every button click or input causes the script to run again from top to bottom, so session state is needed to remember important values like the secret number, score, and attempts. 

The change that finally gave the game a stable secret number was resetting the secret and related game state whenever the difficulty changed, while also keeping the value in `st.session_state`.











## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

One habit I want to reuse in future projects is testing small changes one step at a time instead of changing too many things at once. This project also taught me to use AI for explanation and guidance, but still verify everything myself by running the app and checking the code. Next time, I would ask AI more focused questions and avoid accepting suggestions that are more complex than the bug I am actually fixing. This project changed the way I think about AI-generated code because I learned that AI can be helpful, but its code still needs careful review, testing, and human judgment.










