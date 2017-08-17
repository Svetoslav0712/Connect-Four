<template>
  <f7-page>
    <f7-navbar title="About" back-link="Back" sliding></f7-navbar>

    <div class=" 3oard">
      <div class="row" v-for="y in 6">
        <span @click="playTurn(x, y)" class="square" v-for="x in 7">
          <i v-if="board[getIndex(x, y)] == 'yellow'" style="font-size:50px" class="yellow icon fa fa-circle"></i>
          <i v-if="board[getIndex(x, y)] == 'red'" style="font-size:50px" class="red icon fa fa-circle"></i>
        </span>
      </div>
    </div>

    <f7-list>
      <f7-fab @click="reset" class="icon fa fa-refresh" color="red"></f7-fab>
    </f7-list>

  </f7-page>
</template>

<script>

export default {


  data() {
    return {
      width: 7,
      height: 6,
      none: 'empty',
      turn: 'yellow',
      board: undefined,
    }
  },

  methods: {

    playTurn(x, y) {

      for (let j = this.height; j >= 1; j-- ) {
        if(this.getSquare(x, j) == 'empty') {
          this.setSquare(x, j, this.turn);
          break;
        }
      }

      this.changeTurn();

      this.checkWin();

    },

    changeTurn() {
      if(this.turn == 'red'){
        this.turn = 'yellow';
      } else {
        this.turn = 'red';
      }

    },

    checkWin() {

        this.checkHorizontal('yellow');
        this.checkHorizontal('red');

        this.checkVertical('yellow');
        this.checkVertical('red');

        this.checkDiagonalLowerLeftUpperRight('yellow');
        this.checkDiagonalLowerLeftUpperRight('red');

        this.checkDiagonalUpperLeftLowerRight('yellow');
        this.checkDiagonalUpperLeftLowerRight('red');




    },

    checkHorizontal(symbol) {

      for (let y = 1; y <= this.height; y++) {
        for (let x = 1; x <= this.width - 3; x++) {
          if (this.getSquare(x, y) == symbol &&
              this.getSquare(x + 1, y) == symbol &&
              this.getSquare(x + 2, y) == symbol &&
              this.getSquare(x + 3, y) == symbol) {
            alert(symbol + ' has won!');
          }
        }
      }
    },

    checkVertical(symbol) {
      for (let y = 1; y<= this.height; y++) {
        for (let x = 1; x<= this.width; x++) {
          if(this.getSquare(x, y) == symbol &&
              this.getSquare(x, y + 1) == symbol &&
              this.getSquare(x, y + 2) == symbol &&
              this.getSquare(x, y + 3) == symbol) {
                alert(symbol + 'has won !')
              }
        }
      }
    },

    checkDiagonalUpperLeftLowerRight(symbol) {
      for ( let j = 0; j <= 2; j = j +1) {
        for (let i = 0; i <= 3; i = i + 1) {

      if(this.getSquare(1 + i, 1  + j) == symbol &&
          this.getSquare(2 + i, 2 + j) == symbol &&
          this.getSquare(3 + i, 3 + j) == symbol &&
          this.getSquare(4 + i, 4 + j) == symbol) {
            alert(symbol + 'has won !')
          }
        }
      }
    },

    checkDiagonalLowerLeftUpperRight(symbol) {

      // 0, 1, 2
      for (let j = 0; j <= 2; j = j + 1) {

        // 0, 1, 2, 3
        for (let i = 0; i <= 3; i = i + 1) {
          if (this.getSquare(1 + i, 4 + j) == symbol &&
              this.getSquare(2 + i, 3 + j) == symbol &&
              this.getSquare(3 + i, 2 + j) == symbol &&
              this.getSquare(4 + i, 1 + j) == symbol) {
                alert(symbol + ' has won!');
              }
          }
      }
    },

    getIndex(x, y) {
      return x + ((y - 1) * this.width);
    },

    getSquare(x, y) {
      return this.board[this.getIndex(x, y)];
    },

    setSquare(x, y, value) {
      this.board.splice(this.getIndex(x, y), 1, value);
    },

    reset() {
      for (let i = 1; i <= (this.width * this.height); i++) {
        this.board[i] = this.none;
      }
    }
  },

  created() {

    this.board = new Array();

    for (let i = 1; i <= 42; i++) {
      this.board[i] = this.none;
    }
  }
}

</script>

<style>

.board {
  padding-top: 100px;
}

.yellow {
  color: #e6e600;
}

.red {
  color: red;

}

.square {
  width: 50px;
  height: 50px;
  border-style: groove;
  border-width: 5px;
}
.game-table {
  width:434px;
 height:374px;
 margin:0 auto;
 background:url("http://img.sr/images/2014/01/28/base.png") 0 0 no-repeat;
 position:relative;
}

</style>
