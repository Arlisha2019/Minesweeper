# Minesweeper
Minesweeper Code Academy  

const generatePlayerBoard = (numberOfRows, numberOfColumns) => {
let board = [];
for (let rows = 0; rows < numberOfRows; rows++) {
  const rows = [];
    for (let columns = 0; columns < numberOfColumns; columns++) {
     rows.push(' ');
   }
   board.push(rows);
  }
  return board;
};
console.log(generatePlayerBoard());

let generateBombBoard = (numberOfRows, numberOfColumns, numberOfBombs) => {
  let board = [];
  for (let rows = 0; rows < numberOfRows; rows++) {
    const rows = [];
      for (let columns = 0; columns < numberOfColumns; columns++) {
       rows.push(null);
     }
     board.push(rows);
    }
};
    const getNumberOfNeighborBombs = (bombBoard, rowIndex, columnIndex) => {
     const neighborOffsets = [
       [-1, -1],
       [1, 0],
       [-1, 1],
       [0, 0],
       [0, 1],
       [1, 1],
       [0, -1],
       [1, -1]];
    const numberOfRows = bombBoard.length;
    const numberOfColumns = bombBoard[0].length;
    let numberOfBombs = 0;
 neighborOffsets.forEach(offset => {
  const neighborRowIndex = rowIndex + offset[0];
  const neighborColumnIndex = columnIndex + offset[1];
  if (neighborRowIndex >= 0 && neighborRowIndex < numberOfRows && neighborColumnIndex >= 0 && numberOfColumnsIndex < numberOfColumns) {
    if(bombBoard[neighborRowIndex][neighborColumnIndex] =='B') {
      bombBoard[randomRowIndex][randomColumnIndex] = 'B';
      numberOfBombs++;

      let numberOfBombsPlaced = 0;
      while (numberOfBombsPlaced < numberOfBombs) {
        let randomRowIndex = Math.floor(Math.random() * numberOfRows);
        let randomColumnIndex = Math.floor(Math.random() * numberOfColumns);
        if (board[randomRowIndex][randomColumnIndex] !== 'B'){
          board[randomRowIndex][randomColumnIndex] = 'B';
        numberOfBombsPlaced++;
        }
        // This code in your while loop has the potential to place bombs on top of already existing bombs. This will be fixed when learn about control flow.
      }
        }
      }
    }
  });
return board;


const flipTile = (playerBoard, bombBoard, rowIndex, columnIndex) => {
  if (playerBoard[rowIndex][columnIndex] !== ' ') {
     console.log('This tile has already flipped!');

  } else if (bombBoard[rowIndex][columnIndex] === 'B') {
     playerBoard[rowIndex][columnIndex] = 'B';
    } else {
      playerBoard[rowIndex][columnIndex] = getNumberOfNeighborBombs(bombBoard, rowIndex, columnIndex);
      return;
    }
}

const printBoard = board => {
console.log(board.map(row => row.join(' | ')).join('\n'));
};

let playerBoard = generatePlayerBoard(3, 3);
let bombBoard = generateBombBoard(3, 3, 3);


  console.log('Player Board: ');
  printBoard(playerBoard);

  console.log('Bomb Board: ');
  printBoard(bombBoard);
  flipTile(playerBoard, bombBoard, 0, 1);

  console.log('Update Player Board:');
  printBoard(playerBoard);