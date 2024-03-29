# Tic Tac Toe

Tic Tac Toe (X O) terminal game implementation using Ruby.

## Installation

### Prerequisites

**[Ruby 2.5.0+](https://www.ruby-lang.org/en/downloads/)**

#### RSpec 3.0+

```console
gem install rspec
```

### Install

```console
git clone git@github.com:Nazeh/tic-tac-toe.git
cd tic-tac-toe
```

### Run

**Run game:**

```console
ruby bin/main.rb
```
```console
**************************************************
******** Welcome To Our Tic-Tac-Toe Game! ********
**************************************************
****************** Instructions ******************
** Each player should use an 8 characters name ***
** Choose who will play first, using the X mark **
** Each turn a player will choose a cell to mark *
** Who marks a full row, col or a diagonal wins **
** Players draw, if all cells are marked w/ win **
** You can play again & players' score persist ***
**************************************************
****************                 *****************
****************    7 | 8 | 9    *****************
****************   ---+---+---   *****************
****************    4 | 5 | 6    *****************
****************   ---+---+---   *****************
****************    1 | 2 | 3    *****************
****************                 *****************
********************* Score  *********************
*********** Player 1 : 0  Player 2 : 0 ***********
**************************************************

Player 1: what's your name?  default: Player 1
```

**Run tests:**

```console
rspec
```
See the result in [Specs.md](Specs.md).

## Live version

Play it on **[Repl.it](https://repl.it/@Nazeh1/Tic-Tac-Toe)**

>Slightly slower and doesn't support console clearing.

## How to Play

Board is divided into a grid of 9 cells numbered in a similar
manner to Numpads for convenience!

1. Each player chooses a name or press enter for default name
2. Plyaers choose who gets to play first and get the X mark.
3. Each player chooses an empty cell to mark in their turn.
4. The first player to mark a row, column or diagonal wins.
5. If the grid is full with no winning conditions the game ends with a draw!
6. You can play another match in which case the game will count your score.
7. Otherwise, the game will end and the code will terminate.

## Design

### Board

- **Readable Data**
  - **@board** : 2D Array with 3 rows and 3 columns with numbers 1..9.

- **Public Methods**
  - **#initialize** : initiates @board.
  - **#update**(cell, mark) : updates @board at the given cell with the given mark.
  - **#cell_available?**(cell) : return true if the given cell in @board is not marked, false if otherwise.
  - **#get_row_col_diagonals**(cell) : returns the row, column and all diagonals of given cell in @board.

### Player

- **Readable Data**
  - **@name** : initialized with the instance.
  - **@mark** : only assigned and updated using #add_mark.
  - **@color** : only assigned and updated using #add_mark.
  - **@score** : initialized as Zero.

- **Public Methods**
  - **#initialize**(name) : initiates @name to given name and @score to Zero.
  - **#add_mark**(mark) initiates or updates the player's mark to the given mark and updates color accordingly.
  - **#add_score** : increments @score by 1.

### Game

- **Readable Data**
  - **@status** : initialized with the instance.
  - **@board** : only assigned and updated using #add_mark.
  - **@player1** : only assigned and updated using #add_mark.
  - **@player2** : initialized as Zero.
  - **@current_player** : initialized as Zero.
  
- **Public Methods**
  - **#initialize**(player1, player2, first_player = 1) :
    - initiates:
      - @status = 'continue'
      - @board = new Board instance
      - @player1 = given player1 instance
      - @player2 = given player2 instance
      - updates the first player mark to 'X' and the second to 'O' and assign the first player to @current_player.

  - **#next_move**(cell) :
    - updates @board at the given cell.
    - updates @status.
    - switch @current_player to the next player if @status is still "continue".
    - and finallly, increments the @current_player score.

### Ui module

- **Public Methods**
  - **#prompt_name**(player_number) : Ask player for their name, and returns the first 8 characters, or the given player number if no name was given.
  - **#prompt_first_player**(player1, player2) : Ask players for their choice of who plays first, and return the answer as a digit.
  - **#prompt_cell**(game) : Ask player of his cell choice and returns the answer as a digit if it was a valid unmarked cell.
  - **#play_again?**(game) : Ask the players if they want to play new game, and returns true or false.
  - **#thanks** : outputs a thanks message.

## Author

- **[Ar Nazeh](https://github.com/Nazeh)**
