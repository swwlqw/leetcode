# Largest Number

> [https://leetcode.com/problems/largest-number/](https://leetcode.com/problems/largest-number/)

## Tags

> [Sort](../tags/Sort.md)

## Solutions

### cpp

```cpp
class A
{
public:
    string origin;
    string compare;
    void init(int num)
    {
        stringstream ss;
        ss << num;
        origin = ss.str();
        int len = origin.length();
        int div = 10 / len;
        int mod = 10 % len;
        for (int i=0; i<div; i++)
        {
            compare += origin;
        }
        if (mod)
        {
            compare += origin.substr(0, mod);
        }
    }
};

bool operator<(const A &a1, const A &a2)
{
    return a1.compare.compare(a2.compare) > 0;
}

class Solution
{
public:
    string largestNumber(vector<int>& nums)
    {
        int numsSize = nums.size();
        A as[numsSize];
        for (int i=0; i< numsSize; i++)
        {
            as[i].init(nums[i]);
        }
        sort(as, as + numsSize);
        string re;
        for (int i=0; i< numsSize; i++)
        {
            re += as[i].origin;
        }
        if (re.length()> 0 && re.at(0)=='0')
        {
            re = string("0");
        }
        return re;
    }
};
```

### c

```c
#define TEN 10

typedef struct a{
    char compare[TEN];
    char origin[TEN];
    int size;
} A;

int cmp(const void *a,const void *b){
    char * pa = *((A**)a);
    char * pb = *((A**)b);
    for (int i=0; i< TEN; i++){
        int re =  pb[i]- pa[i];
        if (re){
            return re;
        }
    }
    return 0;
}
char* largestNumber(int* nums, int numsSize)
{
    int len = 0;
    A as[numsSize];
    A* pas[numsSize];

    for (int i=0; i<numsSize; i++){
        int size = sprintf(as[i].origin, "%d", nums[i]);
        as[i].size = size;
        len += size;
        int div = TEN / size;
        int mod = TEN % size;
        char * p = as[i].compare;
        for (int j=0; j< div; j++){
            memcpy(p, as[i].origin, size);
            p += size;
        }
        memcpy(p, as[i].origin, mod);
        pas[i] = as + i;
    }

    qsort(pas, numsSize, sizeof(A*), cmp);

    char * re = malloc(len + 1);
    char * p = re;
    for (int i=0; i<numsSize; i++){
        memcpy(p, pas[i]->origin, pas[i]->size);
        p += pas[i]->size;
    }
    if (re[0]=='0'){
        re[1] = '\0';
    }else{
        *p ='\0';
    }
    return re;
}

```

### java

```java
class A implements Comparable<A> {
	private final String originString;
	private final String compareString;

	public A(int value) {
		originString = String.valueOf(value);
		StringBuilder sb = new StringBuilder();
		while (sb.length() < 10) {
			sb.append(originString);
		}
		sb.setLength(10);
		compareString = sb.toString();
	}

	@Override
	public int compareTo(A o) {
		return o.compareString.compareTo(compareString);
	}

	public String toString() {
		return originString;
	}
	
}

public class Solution {

	public String largestNumber(int[] nums) {
		A[] as = new A[nums.length];
		for (int i = 0; i < nums.length; i++) {
			as[i] = new A(nums[i]);
		}
		Arrays.sort(as);
		StringBuilder sb = new StringBuilder();
		for (A a: as) {
			sb.append(a);
		}
	    String re = sb.toString();
		if (re.startsWith("0")) {
			return "0";
		}
		return re;
	}

}
```