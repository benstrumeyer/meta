## Game Rules

### Game Setup

- Players decide what score they want to play the game to. (Provide quick options: 100, 250, 420, 500, 1337, etc.)
- Each player gets **10** letters to begin with
    - Random letter generation is based on Scrabble [letter distribution ratios](https://en.wikipedia.org/wiki/Scrabble_letter_distributions)


### Game Progression

- Each player can do the following on their turn:
    - Create a [pronounceable](https://github.com/lukem512/pronounceable) word
    - Take the turn to swap their letters (any amount)
    - Skip their turn
- If a word is created by a player, the word is then queried against the NPM database of packages
    - If the word is an exact match, score of the letters are negated from the player's total score
    - If the word is not a match, score is added to the player's total score
    - Otherwise, if the word is a partial match, user's score remains unchanged.
- At the end of a player's turn, if they have fewer than **10** letters in their inventory, the game refills the letters back to **10**.
    - Same letter generation logic as above.
    
### Victory Conditions

- Player reaches pre-determined game score goal.

## Scoring Logic

Score should be based on Scrabble [letter scores](https://en.wikipedia.org/wiki/Scrabble_letter_distributions).

The algorithm is: (sum of letters) * (pronounceability score)

### Multipliers (Combos)

Multipliers apply on the turn of the player while guessing the N-th word in a series of perfect guesses (no-match guesses).

| Correct Guesses | Score multiplier |
|---|---|
| 1 | 1x |
| 2 | 1x |
| 3 | 1.1x |
| 4 | 1.1x |
| 5 | 1.2x |
| 6 | 1.2x |
| 7 | 1.4x |
| 8 | 1.4x |
| 9 | 1.5x |
| 10 | 2x |
   
   
These multipliers also apply to the NEXT word that a player guesses after having guessed N-words wrongly (partial matches count as half, multipliers are only applied to whole number wrong guesses).


