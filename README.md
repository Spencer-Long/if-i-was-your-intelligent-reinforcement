# AI Controlled BlackJack Overview

## Make a Deck
1. 52 cards in a deck
2. [Ace, 2, 3, 4, 5, 6, 7, 8, 9, 10, Jack, Queen, King] * 4

## Create the board
1. Generate a deck (or multiple)
2. Be able to shuffle it
3. Be able to draw from the deck
4. Dealing out cards to "Dealer" and "Player"
   1. First card to dealer is face down
5. Each "person" has a set Chips/money (optional)
   1. Being able to make more or lose money

## The Dealer (controlled by decision tree)
1. If the card total is 16 points or lower, the dealer will always draw another card from the deck.
2. The dealer will continue drawing cards from the deck until the house hand has at least 17 points
3. If the dealer has 17 points off the deal without an Ace, most blackjack rules say the dealer will stand, even if a 21 player has a higher total.
4. The dealer also might have a soft 17 hand, which is one that includes an Ace and any other cards whose combined value totals six points. Both land-based casinos and online blackjack casinos who support live dealer blackjack require dealers to take at least one more card with the dealer has a soft 17 showing. 
5. If the dealer exceeds 21, bust

## Agent (controlled by the AI)
1. Create the observation space
   1. All face up cards
   2. Memory of previous cards (within the scope of the game)
   3. Current chip level (if applicable)
2. Create the action space
   1. Place a bet
      1. $10, $25, $50, $100, etc. (decide on categories)
   2. Hit: take a card
      1. If you split on two ace's, you can't hit again.
   3. Stand: stop at current value
   4. Split: split your starting hand into two if face value is the same, then continue each hand
   5. Double down: only delt one more card (can be used after split), but you pay extra chips. For now, let's make it the same amount, maybe in the future we can let this be variable
   6. Insurance (?)
   7. Surrender (?)
3. Create reward function (scale with the chips)
   1. Positive reward condition
      1. Big reward if you win the hand
      2. Even bigger reward if you win the whole game (win is TBD)
   2. If applicable, negative reward (penalty)
      1. Big penalty if you lose the hand
      2. Even bigger penalty if you lose the game (lose is TBD)
   3. Push (reward, penalty, or neither)
4. Done (win/lose) condition
   1. The hand
      1. Lose: Exceed 21 (bust)
      2. Lose: The dealer has a larger number (but less than 21)
      3. Win: Have a higher hand than the dealer (but less than 21)
      4. Win: The dealer exceeds 21 (bust)
   2. The game
      1. Lose: lose all your chips (amount of games)
      2. Win: you reach a certain amount of chips (ie; $10k)
      3. Lose: exceed game time (in terms of games, real world time, etc.)

## Concerns
1. How to deal with an ace card!
2. How to handle split
3. Push (reward, penalty, or neither)
4. How to scale reward

## Payouts:
> If a player wins a hand they are paid out at 1:1 on the total bet wagered on that hand. For example if the player wagered $10 and then doubled down placing a further bet of $10 on the hand and won, they would be paid a total of $40, their $20 bet back and $20 winnings.
> 
> If the player has Blackjack they are paid at 3:2, so that a wager of $10 the player would be paid a total of $25, their $10 bet back plus $15 winnings.
>
> Should the dealer bust or go over 21 at any point, all the players at the table will win and receive a 1:1 payout.

## Optional:
- Create nice unity environment
- More than one player (AI)