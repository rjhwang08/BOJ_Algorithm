[10866](https://www.acmicpc.net/problem/10866)
- 덱은 스택 또는 큐로도 사용할 수 있다.

1. Java
```java
import java.io.*;
import java.util.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		ArrayDeque<Integer> deque = new ArrayDeque<Integer>();
		int N = Integer.parseInt(br.readLine());

		while(N-- > 0) {
			String input = br.readLine();
			String[] order = input.split(" ");

			if(order[0].equals("push_front")) {
				int num = Integer.parseInt(order[1]);
				deque.offerFirst(num);
			}
			else if(order[0].equals("push_back")) {
				int num = Integer.parseInt(order[1]);
				deque.offerLast(num);
			}
			else if(order[0].equals("pop_front")) {
				if (deque.isEmpty())
					bw.write("-1\n");
				else bw.write(deque.pollFirst().toString() + "\n");
			}
			else if(order[0].equals("pop_back")) {
				if (deque.isEmpty())
					bw.write("-1\n");
				else bw.write(deque.pollLast().toString() + "\n");
			}
			else if(order[0].equals("size"))
				bw.write(String.valueOf(deque.size()) + "\n");
			else if(order[0].equals("empty")) {
				if (deque.isEmpty())
					bw.write("1\n");
				else bw.write("0\n");
			}
			else if(order[0].equals("front")) {
				if (deque.isEmpty())
					bw.write("-1\n");
				else
					bw.write(deque.peekFirst().toString() + "\n");
			}
			else if(order[0].equals("back")) {
				if (deque.isEmpty())
					bw.write("-1\n");
				else
					bw.write(deque.peekLast().toString() + "\n");
			}
		}
		bw.flush();
		bw.close();
		br.close();
	}
}
```
