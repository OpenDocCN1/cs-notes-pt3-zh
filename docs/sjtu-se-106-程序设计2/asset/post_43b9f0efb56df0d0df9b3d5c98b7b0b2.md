
## Deep Blue Beats Gary Kasparov

In 1997, IBM’s Deep Blue program beat Gary Kasparov, who was then the world’s human champion. In 1996, Kasparov had won in play that is in some ways more instructive.

Game 6

Kasparov
30. b6

Deep Blue
30. Bb8 ??

![](img/af430dff16b82a0fe61ce7dee05dcf9c_238_0.png)

## Recursion and Games

- In 1950, Claude Shannon wrote an article for *Scientific American* in which he described how to write a chess-playing computer program.
- Shannon’s strategy was to have the computer try every possible move for white, followed by all of black’s responses, and then all of white’s responses to those moves, and so on.
- Even with modern computers, it is impossible to use this strategy for an entire game, because there are too many possibilities.

![](img/af430dff16b82a0fe61ce7dee05dcf9c_239_0.png)

*Positions evaluated: ~10^53*

... millions of years later ...

## A Simpler Game

- Chess is far too complex a game to serve as a useful example. The text uses a much simpler game called *Nim*, which is representative of a large class of two-player games.
- In Nim, the game begins with a pile of coins between two players. The starting number of coins can vary and should therefore be easy to change in the program.
- In alternating turns, each player takes one, two, or three coins from the pile in the center.
- The player who takes the last coin loses.

## A Sample Game of Nim

There are 11 coins left.
I'll take 2.
There are 9 coins left.
Your move: 1
There are 8 coins left.
I'll take 3.
There are 5 coins left.
Your move: 2
There are 3 coins left.
I'll take 2.
There is only one coin left.
You lose.

![](img/af430dff16b82a0fe61ce7dee05dcf9c_242_0.png)

## Good Moves and Bad Positions

- The essential insight behind the Nim program is bound up in the following mutually recursive definitions:
  - A *good move* is one that leaves your opponent in a bad position.
  - A *bad position* is one that offers no good moves.
- The implementation of the Nim game is really nothing more than a translation of these definitions into code.

## Coding the Nim Strategy

```
/*
 * Looks for a winning move, given the specified number of coins.
 * If there is a winning move in that position, findGoodMove returns
 * that value; if not, the method returns the constant NO_GOOD_MOVE.
 * This implementation depends on the recursive insight that a good move
 * is one that leaves your opponent in a bad position and a bad position
 * is one that offers no good moves.
 */

int findGoodMove(int nCoins) {
    int limit = (nCoins < MAX_MOVE) ? nCoins : MAX_MOVE;
    for (int nTaken = 1; nTaken <= limit; nTaken++) {
        if (isBadPosition(nCoins - nTaken)) return nTaken;
    }
    return NO_GOOD_MOVE;
}

/*
 * Returns true if nCoins is a bad position.  Being left with a single
 * coin is clearly a bad position and represents the simple case.
 */

bool isBadPosition(int nCoins) {
    if (nCoins == 1) return true;
    return findGoodMove(nCoins) == NO_GOOD_MOVE;
}
```

## The Minimax Algorithm

- Games like Nim are simple enough that it is possible to solve them completely in a relatively small amount of time.
- For more complex games, it is necessary to cut off the analysis at some point and then evaluate the position, presumably using some function that looks at a position and returns a *rating* for that position. Positive ratings are good for the player to move; negative ones are bad.
- When your game player searches the tree for best move, it can’t simply choose the one with the highest rating because you control only half the play.
- What you want instead is to choose the move that minimizes the maximum rating available to your opponent. This strategy is called the *minimax* algorithm.

## A Minimax Illustration

- Suppose that the ratings two turns from now are as shown.
- From your perspective, the +9 initially looks attractive.
- Unfortunately, you can’t get there, since the −5 is better for your opponent.
- The best you can do is choose the move that leads to the −2.

![](img/af430dff16b82a0fe61ce7dee05dcf9c_246_0.png)
