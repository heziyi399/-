# -
这一个多月写的题目

#include <iostream>
#include<stdlib.h>
using namespace std;
int main()//木棒三角形 有n根木棍 挑出其中三根构成直角三角形 输出面积最大的三角形面积 输入n再输入每根三角形长度,n<100
{
	int n;//输入n根木棍 再分别输入每根木棍的长度 限制了n数量小于100
	int len[110];//每个数组元素储存木棍长度 且要求长度由小到大给出
	while (scanf("%d", &n) != EOF) 
	{
		for (int i = 0; i < n; i++)
			cin >> len[i];
		double ans = -1;
		for (int i = 0; i < n ; i++)//枚举最短木棍
			for (int j = i + 1; j < n ; j++)
				for (int z = j + 1; j < n ; j++)
				{
					if(len[i]*len[i] + len[j]*len[j]==len[z]*len[z])
					{
						if ((len[i] * len[i] + len[j] * len[j] + len[z] * len[z]) > ans)
							ans = 0.5 * len[i] * len[j];
					}
				}
		if (ans == -1)
			cout << "no !";
		else
			cout << ans;
	}
}
  
  //希尔排序

struct node {
	int key;//简化
}a[20];
int n;//全局变量 排序的数字数目
void print()
{
	for (int i = 0; i < n; i++)
		cout << a[i].key << " ";
}
void create()
{
	int i; n = 0;
	cout << "input keys:";
	cin >> i;
	while (i != -999)
	{
		cin >> i;
		a[n].key = i; n++;
	}
}

void shell(node a[], int n)
{
	int k = n / 2;
	for (int i = n; i >=1; i--)
		a[i].key = a[i-1].key;
	while (k>=1)
	{
		for (int i = k + 1; i <= n; i++)
		{
			a[0].key = a[i].key; int j = i - k;
			
				while(a[j].key>a[0].key&&(j>=0))
				{
					a[j + k].key = a[j].key; j -= k;
				}
				a[j + k] = a[0];
			
		}
		k /= 2;
	}
	for (int i = 0; i <= n; i++)
		a[i].key = a[i + 1].key;
	cout << endl;
	}




int main()
{
	create(); print();
		shell(a,n); print();
}

折半查找
int binarysearch(int array[], int key, int n)
{
	int left = 0;
	int right = n - 1;
	while (left <= right)
	{
		int middle = (left + right) / 2;
		if (array[middle] == key)
			return middle;
		if (left > array[middle])
			left = middle + 1;
		if (right < array[middle])
			right = middle - 1;
	}
	return -1;
}
