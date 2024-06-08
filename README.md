def analyseboard():
   c = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]
   for i in range(0,8):
       if(board[c[i][0]]!=0 and
      board[c[i][0]]==board[c[i][1]]and
      board[c[i][1]]==board[c[i][2]]):
          return board[c[i][0]];
          return 0;

def ConstBoard(board):
  print("THE Current state of the board:\n\n")
  for i in range(0,9):
    if((i>0)and(i%3==0)):  
       print("\n")
    if(board[i]==0):
       print(" _ ",end=" ")
    if(board[i]==1):
       print(" O ",end=" ")
    if(board[i]==-1):
       print(" X ",end=" ")
       print("\n\n")
    
def User1Turn(board):
  pos = input("Enter 'X' POS[1-9]")
  pos = int(pos)
  if(board[pos-1]!=0):
     print("Wrong Move")
     exit(0)
  board[pos-1]=-1
  def User2Turn(board):
      pos = int(input("Enter '0' POS[1-9]"))
  if(board[pos-1]!=0):
     print("Wrong Move")
     exit(0)
  board[pos-1]=1
  
def minmax(board,player):
  x=analyseboard(board)
  if(x!=0):
     return (x*player)
  pos = -1
  value = -2
  for i in range(0,9):
    if(board[i]==0):
      board[i]=player
      score=-minmax(board,player*-1)
      board[i]=0
      if(score>value):
         value=score
         pos=i
      if(pbs==-1):
        return 0
      return value

  
def CompTurn(board):
  pos = -1
  value = -2
  for i in range(0,9):
    if(board[i]==0):
       board[i]=1
       score= -minmax(board,-1)
       board[i]=0
       if(score>value):
          value=score
          pos=i
          board[pos]=1
  
    
def main():
   choice = input("Enter 1 for Single player or 2 for Multiple player: ")
   choice = int(choice)
   board = [0,0,0,0,0,0,0,0,0]
   if(choice==1):
       print("Computer 'O' vs You 'x':\n")
   player=int(input("Enter to play first('1) or second('2'):"))
   for i in range(0,9):
       if(analyseboard(board)!=0):
          break
          if((i+player)%2==0):
           CompTurn(board)
       else:
            ConstBoard(board)
            user1Turn(board)
   else:
        for i in range(0,9):
         if(analyseboard(board)!=0):
          break
          if(1%2==0):
          ConstBoard(board)
         User1Turn(board)
         else:
          ConstBoard(board)
          User2Turn(board)
          
   if(analyseboard(board)==0):
      print("Draw")
   elif(analyseboard(board)==-1):
     print("player:1 has Won")
   else:
     print("player:2 has WOn")
    
     
