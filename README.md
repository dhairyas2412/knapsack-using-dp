# knapsack-using-dp
#include<bits/stdc++.h>
using namespace std;
#define endl "\n"
//a=weight,b=value
int knapsack(int w,int a[],int b[],int n)
{
	int c[n+1][w+1];
	for(int i=0;i<=n;i++)
	{
		for(int j=0;j<=w;j++)
		{
			if(i==0||j==0)
			{
				c[i][j]=0;
			}
			else if(a[i-1]<=j)
			{
				c[i][j]=max(b[i-1]+c[i-1][j-a[i-1]],c[i-1][j]); 
			}
			else
			{
				c[i][j]=c[i-1][j];
			}
		}
	}
	return c[n][w];
}
int main()
{
	//your code goes here
	//ios_base::sync_with_stdio(false);
	//cin.tie(NULL);
	//cout.tie(NULL);
	int t;
	cout << "enter no. of test cases" << endl;
	cin >> t;
	while(t--)
	{
		int w,n;
		cout << "enter total weight" << endl;
		cin >> w;
		cout << "enter no. of objects" << endl;
		cin >> n;
		int a[n],b[n];
		cout << "enter weight" << endl;
		for(int i=0;i<n;i++)
		{
			cin >> a[i];
		}
		cout << "enter values" << endl;
		for(int i=0;i<n;i++)
		{
			cin >> b[i];
		}
		cout << "ans" << " " << knapsack(w,a,b,n) << endl;
	}
	return 0;
}
