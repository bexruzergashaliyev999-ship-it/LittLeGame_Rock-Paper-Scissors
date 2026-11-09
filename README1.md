# Rock-Paper-Scissors AI That Learns From Its Opponent

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/bexruzergashaliyev999-ship-it/LittLeGame_Rock-Paper-Scissors/blob/main/RockPaperScissors.ipynb)

An interactive Rock-Paper-Scissors game in a Jupyter notebook where the computer **adapts to your play style**. It starts by guessing randomly, then keeps a "notebook" of your habits and uses it to pick a counter-move. If you favor one move, the computer notices and starts beating it.

The whole project is one short notebook: `RockPaperScissors.ipynb`. It uses only Python's standard library.

---

## How It Works

1. **Exploration (rounds 1 to 3)**: the computer plays a random move while it has no information about you.
2. **Learning**: after every round, the computer adds one point to the move that would have beaten your choice. For example, if you play rock, the "paper" score goes up.
3. **Exploitation (round 4 onward)**: the computer plays the move with the highest score in its notebook, which is the counter-move to the move you play most often.

```
You play rock  ->  notebook: paper +1  ->  computer's best move becomes paper  ->  paper beats rock
```

| Move | Beaten by |
|------|-----------|
| rock | paper |
| scissors | rock |
| paper | scissors |

This is a simple **frequency-based adaptive strategy**. It shows the core idea behind reinforcement learning (trying moves, collecting feedback and shifting toward what works, balancing exploration and exploitation), but it is not a full reinforcement learning algorithm such as Q-learning.

---

## Example Session

A player who always chooses rock:

```
Rock, scissors or paper? Computer:  rock
Draw
computer's notebook scores:  {'rock': 0, 'scissors': 0, 'paper': 1}

Rock, scissors or paper? Computer:  paper
Computer wins
computer's notebook scores:  {'rock': 0, 'scissors': 0, 'paper': 2}

...

You: 0       Computer: 13
```

The computer quickly locks onto "paper" and wins almost every round. To beat it, vary your moves.

---

## Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/bexruzergashaliyev999-ship-it/LittLeGame_Rock-Paper-Scissors.git
cd LittLeGame_Rock-Paper-Scissors

# 2. (Recommended) Create a virtual environment
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows

# 3. Install Jupyter
pip install -r requirements.txt

# 4. Open the notebook
jupyter notebook RockPaperScissors.ipynb
```

Run the two cells from top to bottom. The second cell asks for your move each round. Type `rock`, `scissors` or `paper`. The notebook also works in Google Colab (upload it and use **Runtime → Run all**).

---

## Game Rules

- The game lasts **15 rounds**.
- An invalid input prints `Invalid input!` and still uses up that round.
- The final score is printed at the end: `You: X      Computer: Y`.

---

## Project Structure

```
.
├── RockPaperScissors.ipynb   # The game
├── requirements.txt
└── README.md
```

---

## Possible Improvements

- Do not count invalid inputs as rounds
- Replace the frequency counter with a real algorithm (for example Q-learning or a multi-armed bandit with epsilon-greedy exploration)
- Look at the player's last few moves (patterns such as "rock, then paper") instead of overall counts
- Break ties between equal scores randomly instead of always picking the first move
- Let the user choose the number of rounds and add a replay option
- Plot the score history over the rounds

---

## License

This project is licensed under the MIT License. Feel free to use, modify and distribute it.
