# Movesets

Pertaining to the creation of the concept of a moveset.

## Generic Format

A moveset consists of a series of transformations to a board:

```javascript
Ptn.parse('3c3>111') => [{
  action: 'pop', count: 3, x: 2, y: 2
}, {
  action: 'push', count: 1, x: 2, y: 3
}, {
  action: 'push', count: 1, x: 2, y: 4
}, {
  action: 'push', count: 1, x: 2, y: 5
}]
```

It's format consists of:

* **action** - Push or Pop pieces from a square
* **count** - Number of pieces to influence
* **x** - X or Column coordinate of influence
* **y** - Y or Row coordinate of influence
* **type** - A special type of piece placement such as a wall or capstone
* **flatten** - If this move attempts to flatten a wall

The X and Y coordinates are provided by applying the direction of the movement to the initial position of the movement.

## Reversing

To undo or reverse a moveset, reverse the list of actions and change all occurrences of `push` to `pop` and vice-versa.

Upon completion of the undo, remaining stack pieces should be restored to the player who had moved in the undo'd turn (or ply) in the case of a placement. This rule is superseded by first turn moves, where it will return to the other
player.

## Applying

A moveset can be applied to a board, but only has the context of a PTN. This means that it is not aware of the board size or pieces on that board. Validity checking still needs to be done to ensure that the moveset is valid in the context of a given board.
