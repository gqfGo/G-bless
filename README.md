# G-bless
Maybe about C++. 
int pre[1010]; //存放第i个元素的父节点
 
int unionsearch(int root) //查找根结点
{
	int son, tmp;
	son = root;
	while(root != pre[root]) //寻找根结点
		root = pre[root];
	while(son != root) //路径压缩
	{
		tmp = pre[son];
		pre[son] = root;
		son = tmp;
	}
	return root;
}
 
void join(int root1, int root2) //判断是否连通，不连通就合并
{
	int x, y;
	x = unionsearch(root1);
	y = unionsearch(root2);
	if(x != y) //如果不连通，就把它们所在的连通分支合并
		pre[x] = y;
}
