[1406](https://www.acmicpc.net/problem/1406)  
- 시간복잡도를 항상 고려할 것!!

1. Java
```java
import java.util.*;
import java.io.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		Stack<Character> left = new Stack<Character>();
		Stack<Character> right = new Stack<Character>();
		
		String input = br.readLine();
		int M = Integer.parseInt(br.readLine());
		
		for(int i=0; i < input.length(); i++)
			left.push(input.charAt(i));
		
		while(M-- > 0) {
			String order = br.readLine();
			char ch = order.charAt(0);
			if(ch == 'L') {
				if(left.size() == 0)
					continue;
				else
					right.push(left.pop());
			}
			else if(ch == 'D') {
				if(right.size() == 0)
					continue;
				else
					left.push(right.pop());
			}
			else if(ch == 'B') {
				if(left.size() == 0)
					continue;
				else
					left.pop();
			}
			else {
				left.push(order.charAt(2));
			}
		}
		
		while(left.isEmpty() == false) {
			right.push(left.pop());
		}
		while(right.isEmpty() == false) {
			bw.write(right.pop());
		}
		bw.flush();
		br.close();
		bw.close();
	}
}
```

2. C++
```c++
#include<stdio.h>
#include<iostream>
#include<string>
#include<stack>
using namespace std;


int main() {
	stack<char> stk_left;
	stack<char> stk_right;
	string s;
	int M;

	cin >> s;
	cin >> M;
	for (char ch : s)
		stk_left.push(ch);

	while (M--) {
		string order;
		cin >> order;
		if (order == "L") {
			if (stk_left.empty())
				continue;
			stk_right.push(stk_left.top());
			stk_left.pop();
		}
		else if (order == "D") {
			if (stk_right.empty())
				continue;
			stk_left.push(stk_right.top());
			stk_right.pop();
		}
		else if (order == "B") {
			if (stk_left.empty())
				continue;
			stk_left.pop();
		}
		else if (order == "P") {
			char c;
			cin >> c;
			stk_left.push(c);
		}
	}

	while (!stk_left.empty()) {
		stk_right.push(stk_left.top());
		stk_left.pop();
	}
	while (!stk_right.empty()) {
		cout << stk_right.top();
		stk_right.pop();
	}
	cout << '\n';

	return 0;
}
```
