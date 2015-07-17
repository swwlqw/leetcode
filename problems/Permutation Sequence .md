# Permutation Sequence

> [https://leetcode.com/problems/permutation-sequence/](https://leetcode.com/problems/permutation-sequence/)

## Tags

> [Backtracking](../tags/Backtracking.md)

> [Math](../tags/Math.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int getNum(int use[], int n, int index) {
    	int k = 0;
    	for (int i = 0; i < n; i++) {
    		if (!use[i]) {
    			if (k == index) {
    				use[i] = 1;
    				return i+1;
    			} else {
    				k++;
    			}
    		}
    	}
    	return 0;
    }
    string getPermutation(int n, int k) {
        int x[n];
    	x[0] = 1;
    	for (int i = 1; i < n; i++) {
    		x[i] = x[i - 1] * i;
    	}
    	string re;
    	int use[n];
    	memset(use, 0, sizeof(use));
    	int j = 0;
    	k -= 1;
    	for (int i = n - 1; i >= 0; i--) {
    		int index = k / x[i];
    		k = k % x[i];
    		int num = getNum(use, n, index);
    		re += (char)(num + '0');
    	}
    	return re;
    }
};
```

### c

```c
int getNum(int use[], int n, int index) {
	int k = 0;
	for (int i = 0; i < n; i++) {
		if (!use[i]) {
			if (k == index) {
				use[i] = 1;
				return i+1;
			} else {
				k++;
			}
		}
	}
	return 0;
}

char* getPermutation(int n, int k) {
	int x[n];
	x[0] = 1;
	for (int i = 1; i < n; i++) {
		x[i] = x[i - 1] * i;
	}
	char* re = malloc(n+1);
	int use[n];
	memset(use, 0, sizeof(use));
	int j = 0;
	k -= 1;
	for (int i = n - 1; i >= 0; i--) {
		int index = k / x[i];
		k = k % x[i];
		int num = getNum(use, n, index);
		re[j++] = (char)(num + '0');
	}
	re[j++]='\0';
	return re;
}
```

### java

```java
public class Solution {
    public String getPermutation(int n, int k) {
		int[] x = new int[n];
		x[0] = 1;
		for (int i = 1; i < n; i++) {
			x[i] = x[i - 1] * i;
		}
		StringBuilder sb = new StringBuilder();
		boolean[] use = new boolean[n];
		k -= 1;
		for (int i = n - 1; i >= 0; i--) {
			int index = k / x[i];
			k = k % x[i];
			int num = getNum(use, index);
			sb.append(num);
		}
		return sb.toString();
	}

	private int getNum(boolean[] use, int index) {
		int k = 0;
		for (int i = 0; i < use.length; i++) {
			if (!use[i]) {
				if (k == index) {
					use[i] = true;
					return i+1;
				} else {
					k++;
				}
			}
		}
		return 0;
	}
}
```