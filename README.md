# dijkshtr

//Dijkstra alorithm//

#include <stdio.h>
#include<stdio.h>
#define INFINITY 9999
#define MAX 10
void dijikstra(int G[MAX][MAX], int n, int startnode)
	{
		int cost[MAX][MAX], distance[MAX], pred[MAX];
		int visited[MAX], count, mindistance, nextnode, i,j;
			for(i=0;i < n;i++)
			{
				for(j=0;j < n;j++)
				{
					if(G[i][j]==0)
					{
						cost[i][j]=INFINITY;
					}
					else
					{
						cost[i][j]=G[i][j];
					}
			}
		}
	
			for(i=0;i< n;i++)
			{
				distance[i]=cost[startnode][i];
				pred[i]=startnode;
				visited[i]=0;
			}
				distance[startnode]=0;
				visited[startnode]=1;
				count=1;
				while(count < n-1)
				{
					mindistance=INFINITY;
					for(i=0;i < n;i++)
					{
						if(distance[i] < mindistance&&!visited[i])
						{
							mindistance=distance[i];
							nextnode=i;
						}
					}
							visited[nextnode]=1;
							for(i=0;i < n;i++)
							{
								if(!visited[i])
								{
									if(mindistance+cost[nextnode][i] < distance[i])
									{
										distance[i]=mindistance+cost[nextnode][i];
										pred[i]=nextnode;
									}
								}
							}
											count++;
						}
										for(i=0; i < n; i++)
									    {
											if(i!=startnode)
											{
												printf("\nDistance of V%d = %d", i, distance[i]);
												printf("\nPath : V%d", i);
												j=i;
												do
												{
													j=pred[j];
													printf(" <-V%d ", j);
                                                }
    											while(j!=startnode);
    											}
											}
										}
										int main()
										{
											int i, j, n, u;
											/* TYPE HERE YOUR ADJACENCY MATRIX */
											int G[MAX][MAX]={
											{0,5,10,0,7},
											{0,0,3,9,2},
											{0,2,0,1,0},
											{0,0,0,0,4},
											{0,0,0,6,0}
											};
												printf("\nEnter the no. of vertices:: ");
												scanf("%d", &n);
												/* 
												printf("\nEnter the adjacency matrix::\n");
												for(i=0;i < n;i++)
												for(j=0;j < n;j++)
												scanf("%d", &G[i][j]);
												*/
												printf("\nEnter the starting node: ");
												scanf("%d", &u);
												dijikstra(G,n,u);
											}
/*
OUTPUT
Enter the no. of vertices:: 5
Enter the starting node:: 0
Distance of V1 = 5
Path : V1 <-V0
Distance of V2 = 8
Path : V2 <-V1 <-V0
Distance of V3 = 9
Path : V3 <-V2 <-V1 <-V0
Distance of V4 = 7
Path : V4 <-V0
*/
