# PTN

Playtak Notation, the standard invented by BenWo for expressing moves in a Tak game.

## Components

```javascript
Ptn {
  ptn: '3c3>111',
  pieceCount: '3',
  specialPiece: undefined,
  column: 'c',
  row: '3',
  movement: '>111',
  direction: '>',
  distribution: '111',
  wallSmash: undefined,
  pieceType: 'piece',
  x: 2,
  y: 2
}
```

PTN consists of:

* `c3` - A piece location, or the placement of a piece
* `3c3` - The number of pieces to move
* `3c3>` - The direction of the movement
* `3c3>111` - The distribution of pieces for that movement
* `Cc3` - The placement of a Capstone
* `Sc3` - The placement of a Standing Stone, or Wall.

## Additions

Proposals have been made for a wall-flattening indicator to be added to PTN. Currently this indicator is `*`:

```
3c3>111*
```

Where `*` is a suffix operator indicating that a wall has been flattened. This is added to ease the creation of bots and other automated tools, as well as make PTN logs more easily human readable at a glance.

Currently `*` is only implemented in `OpenTak` libraries, and consensus has not been reached on the exact character to use.
