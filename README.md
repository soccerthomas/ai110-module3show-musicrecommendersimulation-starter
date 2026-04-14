# 🎵 Music Recommender Simulation

## Project Summary

In this project you will build and explain a small music recommender system.

Your goal is to:

- Represent songs and a user "taste profile" as data
- Design a scoring rule that turns that data into recommendations
- Evaluate what your system gets right and wrong
- Reflect on how this mirrors real world AI recommenders

Replace this paragraph with your own summary of what your version does.

---

## How The System Works

Explain your design in plain language.

Some prompts to answer:

- What features does each `Song` use in your system
  - For example: genre, mood, energy, tempo
- What information does your `UserProfile` store
- How does your `Recommender` compute a score for each song
- How do you choose which songs to recommend

You can include a simple diagram or bullet list if helpful.
Each song has a genre, mood, energy, and tempo. The user picks their preferences for those same things. The recommender scores every song by how well it matches those preferences, then returns the top results.
---

## Getting Started

### Setup

1. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Mac or Linux
   .venv\Scripts\activate         # Windows

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python -m src.main
```

### Running Tests

Run the starter tests with:

```bash
pytest
```

You can add more tests in `tests/test_recommender.py`.

---

## Experiments You Tried

Use this section to document the experiments you ran. For example:

- What happened when you changed the weight on genre from 2.0 to 0.5
- What happened when you added tempo or valence to the score
- How did your system behave for different types of users experiments you tried
  
Lowering the genre weight from 2.0 to 0.5 made the results more diverse but sometimes returned songs that felt mismatched. Adding tempo as a scored feature helped separate high-energy tracks from slower ones even within the same genre. Testing with a "calm" user profile versus an "energetic" one produced noticeably different results. The calm profile surfaced low-energy, slow-tempo songs while the energetic profile returned fast, intense tracks.

---

## Limitations and Risks

Summarize some limitations of your recommender.

Examples:

- It only works on a tiny catalog
- It does not understand lyrics or language
- It might over favor one genre or mood

You will go deeper on this in your model card.
Only works on a small catalog so recommendations repeat quickly
Can over-favor one genre or mood if weights are off
Does not learn from skips or replays
---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

Write 1 to 2 paragraphs here about what you learned:

- about how recommenders turn data into predictions
- about where bias or unfairness could show up in systems like this


---

## 7. `model_card_template.md`

Combines reflection and model card framing from the Module 3 guidance. :contentReference[oaicite:2]{index=2}  

```markdown
# 🎧 Model Card - Music Recommender Simulation

## 1. Model Name

Give your recommender a name, for example:

> AudioGI

---

## 2. Intended Use

- What is this system trying to do
- Who is it for
This recommender suggests songs from a small catalog based on a user's preferred genre, mood, energy, and tempo. It assumes the user can describe their taste upfront and that those preferences stay consistent. This is a classroom exploration project, not a production system.
Example:

> This model suggests 3 to 5 songs from a small catalog based on a user's preferred genre, mood, and energy level. It is for classroom exploration only, not for real users.

---

## 3. How It Works (Short Explanation)

Describe your scoring logic in plain language.

- What features of each song does it consider
- What information about the user does it use
- How does it turn those into a number

Try to avoid code in this section, treat it like an explanation to a non programmer.
Each song has four attributes: genre, mood, energy, and tempo. The user provides their ideal values for each. Genre and mood get a fixed bonus for a match, while energy and tempo are scored by how close the numbers are. Songs that match on more things score higher and get recommended first
---

## 4. Data

Describe your dataset.

- How many songs are in `data/songs.csv`
- Did you add or remove any songs
- What kinds of genres or moods are represented
- Whose taste does this data mostly reflect
The catalog contains a small set of songs from songs.csv covering a handful of genres like Hip-Hop, Pop, and Rock, with moods like Energetic, Chill, and Happy. No songs were added or removed. The dataset is limited and likely reflects mainstream Western music taste, leaving out a lot of genres and cultural variety.
---

## 5. Strengths

Where does your recommender work well

You can think about:
- Situations where the top results "felt right"
- Particular user profiles it served well
- Simplicity or transparency benefits

---
Works well for users with clear, consistent preferences. The scoring is transparent and easy to reason about. Simple user profiles with strong genre or mood preferences tend to produce intuitive recommendations.

## 6. Limitations and Bias

Where does your recommender struggle

Some prompts:
- Does it ignore some genres or moods
- Does it treat all users as if they have the same taste shape
- Is it biased toward high energy or one genre by default
- How could this be unfair if used in a real product
The catalog is tiny so results repeat quickly. The system ignores lyrics, artist style, tempo feel, and cultural context. It treats all users as having one fixed taste profile, so it can't handle moods that shift. High genre weights can drown out energy and tempo signals, and underrepresented genres in the dataset will rarely surface regardless of user preference.
---

## 7. Evaluation

How did you check your system

Examples:
- You tried multiple user profiles and wrote down whether the results matched your expectations
- You compared your simulation to what a real app like Spotify or YouTube tends to recommend
- You wrote tests for your scoring logic

You do not need a numeric metric, but if you used one, explain what it measures.
The calm profile consistently returned low-energy slow songs while the energetic profile returned fast tracks, which matched expectations. Adjusting genre weight from 2.0 to 0.5 noticeably changed result diversity.
---

## 8. Future Work

If you had more time, how would you improve this recommender

Examples:

- Add support for multiple users and "group vibe" recommendations
- Balance diversity of songs instead of always picking the closest match
- Use more features, like tempo ranges or lyric themes
Add a feedback loop so the system learns from skips and replays
Support tempo ranges instead of a single target value
---

## 9. Personal Reflection

A few sentences about what you learned:

- What surprised you about how your system behaved
- How did building this change how you think about real music recommenders
- Where do you think human judgment still matters, even if the model seems "smart"
The most interesting thing was realizing how easy it is for bias to sneak in through the data itself. If certain genres are underrepresented in the catalog, the system will never recommend them no matter how well they'd match a user's actual taste. Building this showed me how recommenders reduce something as personal as music taste down to a few numbers.

