<h1>ExpNo 7 : Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name: Pranav K    </h3>
<h3>Register Number: 2305001026     </h3>
<H3>Aim:</H3>
<p>
Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>
<h1>GOALS of Alpha-Beta Pruning in MiniMax Search Algorithm</h1>

<h3>Improve the decision-making efficiency of the computer player by reducing the number of evaluated nodes in the game tree.</h3>
<h3>Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning and the Minimax algorithm with Python Code.</h3>
<h1>IMPLEMENTATION</h1>

The project involves developing a Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning with the Minimax algorithm. Using this algorithm, the computer player analyzes the game state, evaluates possible moves, and selects the optimal action based on the anticipated outcomes.

<h1>The Minimax algorithm</h1>

recursively evaluates all possible moves and their potential outcomes, creating a game tree.

<h1>Alpha-Beta pruning</h1>

Alpha–Beta (𝛼−𝛽) algorithm is actually an improved minimax using a heuristic. It stops evaluating a move when it makes sure that it’s worse than a previously examined move. Such moves need not to be evaluated further.

When added to a simple minimax algorithm, it gives the same output but cuts off certain branches that can’t possibly affect the final decision — dramatically improving the performance

## PROGRAM
```python
import math

def win(b):  # check winner
    for x,y,z in [(0,1,2),(3,4,5),(6,7,8),(0,3,6),(1,4,7),(2,5,8),(0,4,8),(2,4,6)]:
        if b[x]==b[y]==b[z] and b[x]!=' ': return b[x]
    return None

def minimax(b, depth, maxP, a, bta):
    w = win(b)
    if w=='X': return 10-depth
    if w=='O': return depth-10
    if ' ' not in b: return 0

    if maxP:
        best=-math.inf
        for i in range(9):
            if b[i]==' ':
                b[i]='X'
                best=max(best,minimax(b,depth+1,False,a,bta))
                b[i]=' '
                a=max(a,best)
                if bta<=a: break
        return best
    else:
        best=math.inf
        for i in range(9):
            if b[i]==' ':
                b[i]='O'
                best=min(best,minimax(b,depth+1,True,a,bta))
                b[i]=' '
                bta=min(bta,best)
                if bta<=a: break
        return best

def best_move(b):
    mv=-1; val=-math.inf
    for i in range(9):
        if b[i]==' ':
            b[i]='X'
            score=minimax(b,0,False,-math.inf,math.inf)
            b[i]=' '
            if score>val: val=score; mv=i
    return mv

# Example
board=['X','O','X','O','O',' ','X',' ',' ']
print("Board:")
for i in range(0,9,3): print(board[i:i+3])
m=best_move(board)
print("\nBest move for X:",m)

```
<hr>
<h2> Output:</h2>

<img width="216" height="133" alt="image" src="https://github.com/user-attachments/assets/94b8735e-152c-4b81-9949-f1a72380a194" />


## RESULT
We have successfully implemented Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game.
