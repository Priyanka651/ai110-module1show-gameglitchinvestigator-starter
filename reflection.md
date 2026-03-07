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

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
