import java.util.Scanner;
//0 means blank
//1 means "*"
//2 means "o"

//choice is the members move
public class TicTacToe {
    static void displayBoard(int a[][])
    {
        int i,j;
        for(i=0;i<3;i++)
        {
            for(j=0;j<3;j++)
            {
                if(a[i][j]==0)
                {
                    System.out.print("-");
                }
                else if(a[i][j]==1)
                {
                    System.out.print("*");
                }
                else
                {
                    System.out.print("o");
                }
                System.out.print(" ");
            }
            System.out.println();
        }
    }
    static boolean checkBoard(int a[][])
    {
        for(int i=0;i<3;i++)
        {
            for(int j=0;j<3;j++)
            {
                if(a[i][j]==0)
                {
                    return false;
                }
            }
        }
        return true;
    }
    static boolean checkRow(int a[][],int r,int choice){
        int i,j;
        for(i=0;i<3;i++)
        {
            if(a[r][i] != choice)
            {
                return false;
            }
        }
        return true;
    }
    static boolean checkCol(int a[][],int c,int choice){
        int i,j;
        for(i=0;i<3;i++)
        {
            if(a[i][c] != choice)
            {
                return false;
            }
        }
        return true;
    }
    static boolean checkMainDiagonal(int a[][],int choice)
    {
        int i;
        for(i=0;i<3;i++)
        {
            if(a[i][i]!=choice)
            {
                return false;
            }
        }
        return true;
    }
    static boolean checkNonMainDiagonal(int a[][],int choice)
    {
        int i;
        for(i=0;i<3;i++)
        {
            if(a[i][2-i]!=choice)
            {
                return false;
            }
        }
        return true;
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        System.out.println("Welcome to your in Tic-Tac-Toe");
        int a[][]=new int[3][3];
        int i,j;
        boolean turn=false;
        int choice;
        while(true)
        {
            if(checkBoard(a))
            {
                System.out.println("Match Drawn :)");
                break;
            }

            if(turn==false)
            {
                choice=1;
                System.out.println("Turn of *");
            }
            else
            {
                System.out.println("Turn of o");
                choice=2;
            }
            System.out.println("Enter the numbers in this format:");
            System.out.println("7 8 9");
            System.out.println("4 5 6");
            System.out.println("1 2 3");
            System.out.println("Enter the choice:");
            int num=sc.nextInt();
            if(num==7)
            {
                i=0;j=0;
            }
            else if(num==8)
            {
                i=0;j=1;
            }
            else if(num==9)
            {
                i=0;j=2;
            }
            else if(num==4)
            {
                i=1;j=0;
            }
            else if(num==5)
            {
                i=1;j=1;
            }
            else if(num==6)
            {
                i=1;j=2;
            }
            else if(num==1)
            {
                i=2;j=0;
            }
            else if(num==2)
            {
                i=2;j=1;
            }
            else
            {
                i=2;j=2;
            }
            if(a[i][j]==1||a[i][j]==2)
            {
                System.out.println("Oops!You mistakenly typed it");
                continue;
            }
            else
            {
                a[i][j]=choice;
                displayBoard(a);
                if(checkMainDiagonal(a,choice)||checkNonMainDiagonal(a,choice)||checkCol(a,j,choice)||checkRow(a,i,choice)) {
                    if(choice==1)
                    {
                        System.out.println("Congratulation! * win this game");
                    }
                    else
                    {
                        System.out.println("Congratulation! o win this game");
                    }
                    break;
                }
            }
            turn=!turn;
        }
    }
}
