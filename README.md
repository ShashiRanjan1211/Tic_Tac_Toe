# TicTacToe
Introduction
To solve games using AI, we will introduce the concept of a game tree followed by minimax algorithm. The different states of the game are represented by nodes in the game tree, very similar to the above planning problems. The idea is just slightly different. In the game tree, the nodes are arranged in levels that correspond to each player's turns in the game so that the “root” node of the tree (usually depicted at the top of the diagram) is the beginning position in the game. In tic-tac-toe, this would be the empty grid with no Xs or Os played yet. Under root, on the second level, there are the possible states that can result from the first player’s moves, be it X or O. We call these nodes the “children” of the root node.

Each node on the second level, would further have as its children nodes the states that can be reached from it by the opposing player's moves. This is continued, level by level, until reaching states where the game is over. In tic-tac-toe, this means that either one of the players gets a line of three and wins, or the board is full and the game ends in a tie.

### Combinatorics :
When considering only the state of the board, and after taking into account board symmetries (i.e. rotations and reflections),
there are only 138 terminal board positions. A combinatorics study of the game shows that when "X" makes the first move every 
time, the game is won as follows :

>* 91 distinct positions are won by (X)<br>
>* 44 distinct positions are won by (O)<br>
>* 3 distinct positions are drawn (often called a "cat's game")

### Pseudocode
~~~~
function minimax(node, depth, isMaximizingPlayer, alpha, beta):

    if node is a leaf node :
        return value of the node
    
    if isMaximizingPlayer :
        bestVal = -INFINITY 
        for each child node :
            value = minimax(node, depth+1, false, alpha, beta)
            bestVal = max( bestVal, value) 
            alpha = max( alpha, bestVal)
            if beta <= alpha:
                break
        return bestVal

    else :
        bestVal = +INFINITY 
        for each child node :
            value = minimax(node, depth+1, true, alpha, beta)
            bestVal = min( bestVal, value) 
            beta = min( beta, bestVal)
            if beta <= alpha:
                break
        return bestVal
        
// Calling the function for the first time.
minimax(0, 0, true, -INFINITY, +INFINITY)
~~~~

### Minimax Algorithm Visualisation
![alt text](https://github.com/Prajwal-P/TicTacToe-with-AI/blob/master/MiniMax-algorithm.png)

### Instructions to run:
#### Windows
1. Install a cpp compiler
2. Open commmand prompt in the folder where program is saved
3. `g++ ai.cpp` then `./a`

#### Linux
1. Install a cpp compiler
2. Open terminal in the folder where program is saved
3. `g++ ai.cpp` then `./a.out`
