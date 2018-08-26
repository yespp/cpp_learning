#include<iostream>
#include<string>
using namespace std;

//求next 相当于字符串自己跟自己比，前i位的前后缀最大公共长度，从第1位开始比往右边移动.//跳转next[i] 相当于右移动j-next[i];
//再强调一遍，我们这样求出来的F值是该最长相同前缀后缀中的前缀的结束字符的数组位置（从０开始编号），如果要求最长相同前缀后缀的长度，要输出F[i]+1。
//1.next[0]=-1　(虽说这里应该是０，但为了方便判越界，同时为了方便判断第０位与第i位，程序中这里置为-1)
//2.这是一个从前往后的线性推导，所以在计算next[i]时可以保证next[0]~next[i - 1]都是已经计算出来的了
//3.若以某一位结尾的子串不存在相同的前缀和后缀，这个位的next置为 - 1（这里置为 - 1的原因同第一条一样）
//next[i]=0表示最长相同前缀后缀长度为１，即真实的最长相同前缀后缀＝next[i]+1。(重要的内容要放大)
//为什么要这样设置呢，因为这时next[i]代表的就不仅仅与前后缀长度有关了，它还代表着这个前缀的最后一个字符在子串B中的位置。
//在把最长相同前缀后缀数组整体向右偏移1位，把第0位的值设成-1，就是next数组，next[0]=-1，这只是为了编程的方便，并没有其他的意义。


//如果要求最长相同前缀后缀的长度，要输出F[i]+1。
void getnext(const string& s, int next[], int len){//求next就是自己匹配自己
    int t;
    next[0] = -1;          //-1代表不存在最长公共前后缀
    for (int i = 1; i < len; ++i){
        t = next[i - 1];
        while (s[t + 1] != s[i] && t>0){//如果下一个不同，那么t就变成next[t]，注意next[t]是小于t的，无论t取任何值。
        t = next[t];//回溯
		}
		//完了之后就是判断next[i]了
		if (s[t + 1] == s[i])next[i] = t + 1;//这两行其实就等于如果是s[t+1]=s[i],t自增，不等则不变 然后next[i]=t; 
		//上面一句其实就是next[i]=next[i-1]+1;
		else next[i] = -1;

	}
	//cout <<s<< endl;
	for(int i=0;i<len;++i)cout << next[i] <<" ";//next数组之加1，就表示当前字符的前后缀最大值公共元素长度
	cout << endl;

}
void kmp(const string& s1, const string&s2){
	int* next = new int[100005];
	int l2 = s2.length();
	int l1 = s1.length();
	getnext(s1, next,l1);
	int i = 0, j = 0;
	while (j < l2)
	{
		if (s1[i] == s2[j]){
			++i; ++j;
			if (i == l1){ cout << j - 1 << "wancheng"; i = next[i-1]+1; }//输出完成匹配时候的位置的下标，也可以在这里作别的算个数之类的。。。
		}
		else
		{
			if (i == 0)++j;//模板串开头不能则直接将目标串左移
			else
			{
				i = next[i-1]+1;//跳转i=next[i-1]+1;i=next[i]+1似乎都可以
			}
		}
	}
	delete[]next;
	next = nullptr;
}

	int main()
	{
	string s1, s2;
	while (cin >> s1 >> s2)kmp(s1, s2);
   // system("pause");
	}

















