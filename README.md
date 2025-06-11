# Snake-Game
//            snake Game
#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
int height=20,width=30,x,y,fruitX,fruitY,flag,gameEnd,score;
int tailX[100],tailY[100];
int piece=0;
void makelogic()
{
	int i;
	int prevx,prevy,prev2x,prev2y;
	prevx=tailX[0];
	prevy=tailY[0];
	tailX[0]=x;
	tailY[0]=y;
	for(i=1;i<=piece;i++)
	{
		prev2x=tailX[i];
		prev2y=tailY[i];
		tailX[i]=prevx;
		tailY[i]=prevy;
		prevx=prev2x;
		prevy=prev2y;
	}
	switch(flag)
	{
		case 1:
			{
				x--;
				break;
			}
			case 2:
			{
				x++;
				break;
			}
			case 3:
				{
					y--;
					break;
				}
				case 4:
					{
						y++;
						break;
					}
	}
	if(x==0||x==height||y==0||y==width)
	{
		gameEnd=1;
	}
	if(x==fruitX && y==fruitY)
	{
		
	label3:
	fruitX=rand()%20;
	if(fruitX==0)
	goto label3;
	
		label4:
	fruitY=rand()%20;
	if(fruitY==0)
	goto label4;
	score+=score;
	piece++;
	}
}
void input()
{
	if(kbhit())
	{
		switch(getch())
		{
			case 'w':
			{
				flag=1;
				break;
			}
				case 's':
			{
				flag=2;
				break;
			}
				case 'a':
			{
				flag=3;
				break;
			}
				case 'd':
			{
				flag=4;
				break;
			}
		}
	}
}
void setup()
{
	x= height/2;
	y=width/2;
	
	label1:
	fruitX=rand()%20;
	if(fruitX==0)
	goto label1;
	
		label2:
	fruitY=rand()%20;
	if(fruitY==0)
	goto label2;
	gameEnd=0;
	score+=10;
	piece++;
}
void draw()
{
	system("cls");//alternative of clrscr();
	printf("\t==> MZR & zeeshan PROJECT<==");
	printf("\n \t==>SNAKE GAME<==\n \n");
	int i,j,k,ch;
	for(i=0;i<height;i++)
	{
		for(j=0;j<width;j++)
	{
		if(i==0 || i==height || j==0 || j==width)
		{
				printf("!");
		}
		else
		{
			if(i==x&&j==y)
			{
				printf("^");
			}
			else if(i==fruitX && j==fruitY)
			{
				printf("<3");
			}
			else
			{
				ch=0;
				for(k=0;k<piece;k++)
				{
					if(i==tailX[k]&&j== tailY[k])
					{
						printf("#");
						ch=1;
					}
				}
					printf(" ");
			}
		
		}
		
	}

		printf("\n");
	}
printf("your score is \t %d",score);
}
int main()
{
	setup();
	while(gameEnd!=1)
	{
			input();
	draw();
	makelogic();
	}
	input();
	draw();
	makelogic();
}

