# Median of Two Sorted Arrays

> [https://leetcode.com/problems/median-of-two-sorted-arrays/](https://leetcode.com/problems/median-of-two-sorted-arrays/)

## Tags

> [Divide and Conquer](../tags/Divide and Conquer.md)

> [Array](../tags/Array.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
private:
    int findIndex(vector<int>& nums1, vector<int>& nums2, int k, int start, int end) {
		if (start == end - 1) {
			return start;
		}
		int mid = (start + end) / 2;
		if (k == mid) {
			int v1 = nums1[mid - 1];
			if (nums2.size() > 0 && v1 > nums2[0]) {
				return findIndex(nums1, nums2, k, start, mid);
			} else {
				return mid;
			}
		}
		int v1 = nums1[mid - 1];
		int v2 = nums2[k - mid - 1];
		if (v1 == v2) {
			return mid;
		} else if (v1 > v2) {
			if (k - mid < nums2.size() && v1 > nums2[k - mid]) {
				return findIndex(nums1, nums2, k, start, mid);
			} else {
				return mid;
			}
		} else {
			if (mid < nums1.size() && v2 > nums1[mid]) {
				return findIndex(nums1, nums2, k, mid, end);
			} else {
				return mid;
			}
		}
	}

    int getValue(vector<int>& nums1, vector<int>& nums2, int index1, int index2) {
		if (index1 > nums1.size()) {
			return nums2[index2];
		} else if (index2 > nums2.size()) {
			return nums1[index1];
		} else if (index1 == 0) {
			return nums2[index2 - 1];
		} else if (index2 == 0) {
			return nums1[index1 - 1];
		} else {
			return max(nums1[index1 - 1], nums2[index2 - 1]);
		}
	}
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int m = nums1.size();
		int n = nums2.size();
		int sum = m + n;
		int half = (sum + 1) / 2;
		int start = max(0, half - n);
		int end = min(m, half);
		int index = findIndex(nums1, nums2, half, start, end + 1);
		int value = getValue(nums1, nums2, index, half - index);
		if (sum % 2 == 1) {
			return value;
		} else {
			int v1 = getValue(nums1, nums2, index + 1, half - index);
			int v2 = getValue(nums1, nums2, index, half - index + 1);
			double re = value + min(v1, v2);
			return re / 2;
		}
    }
};
```

### c

```c
int max(int a, int b){
    return a > b ? a : b;
}

int min(int a, int b){
    return a < b ? a : b;
}

int findIndex(int* nums1, int* nums2, int k, int start, int end, int nums1Size, int nums2Size) {
	if (start == end - 1) {
		return start;
	}
	int mid = (start + end) / 2;
	if (k == mid) {
		int v1 = nums1[mid - 1];
		if (nums2Size > 0 && v1 > nums2[0]) {
			return findIndex(nums1, nums2, k, start, mid, nums1Size, nums2Size);
		} else {
			return mid;
		}
	}
	int v1 = nums1[mid - 1];
	int v2 = nums2[k - mid - 1];
	if (v1 == v2) {
		return mid;
	} else if (v1 > v2) {
		if (k - mid < nums2Size && v1 > nums2[k - mid]) {
			return findIndex(nums1, nums2, k, start, mid, nums1Size, nums2Size);
		} else {
			return mid;
		}
	} else {
		if (mid < nums1Size && v2 > nums1[mid]) {
			return findIndex(nums1, nums2, k, mid, end, nums1Size, nums2Size);
		} else {
			return mid;
		}
	}
}

int getValue(int* nums1, int* nums2, int index1, int index2, int nums1Size, int nums2Size) {
	if (index1 > nums1Size) {
		return nums2[index2];
	} else if (index2 > nums2Size) {
		return nums1[index1];
	} else if (index1 == 0) {
		return nums2[index2 - 1];
	} else if (index2 == 0) {
		return nums1[index1 - 1];
	} else {
		return max(nums1[index1 - 1], nums2[index2 - 1]);
	}
}

double findMedianSortedArrays(int* nums1, int nums1Size, int* nums2, int nums2Size) {
    int sum = nums1Size + nums2Size;
	int half = (sum + 1) / 2;
	int start = max(0, half - nums2Size);
	int end = min(nums1Size, half);
	int index = findIndex(nums1, nums2, half, start, end + 1, nums1Size, nums2Size);
	int value = getValue(nums1, nums2, index, half - index, nums1Size, nums2Size);
	if (sum % 2 == 1) {
		return value;
	} else {
		int v1 = getValue(nums1, nums2, index + 1, half - index, nums1Size, nums2Size);
		int v2 = getValue(nums1, nums2, index, half - index + 1, nums1Size, nums2Size);
		double re = value + min(v1, v2);
		return re / 2;
	}
}
```

### java

```java
public class Solution {

	private int findIndex(int[] nums1, int[] nums2, int k, int start, int end) {
		if (start == end - 1) {
			return start;
		}
		int mid = (start + end) / 2;
		if (k == mid) {
			int v1 = nums1[mid - 1];
			if (nums2.length > 0 && v1 > nums2[0]) {
				return findIndex(nums1, nums2, k, start, mid);
			} else {
				return mid;
			}
		}
		int v1 = nums1[mid - 1];
		int v2 = nums2[k - mid - 1];
		if (v1 == v2) {
			return mid;
		} else if (v1 > v2) {
			if (k - mid < nums2.length && v1 > nums2[k - mid]) {
				return findIndex(nums1, nums2, k, start, mid);
			} else {
				return mid;
			}
		} else {
			if (mid < nums1.length && v2 > nums1[mid]) {
				return findIndex(nums1, nums2, k, mid, end);
			} else {
				return mid;
			}
		}
	}

	private int getValue(int[] nums1, int[] nums2, int index1, int index2) {
		if (index1 > nums1.length) {
			return nums2[index2];
		} else if (index2 > nums2.length) {
			return nums1[index1];
		} else if (index1 == 0) {
			return nums2[index2 - 1];
		} else if (index2 == 0) {
			return nums1[index1 - 1];
		} else {
			return Math.max(nums1[index1 - 1], nums2[index2 - 1]);
		}
	}

	public double findMedianSortedArrays(int[] nums1, int[] nums2) {
		int m = nums1.length;
		int n = nums2.length;
		int sum = m + n;
		int half = (sum + 1) / 2;
		int start = Math.max(0, half - n);
		int end = Math.min(m, half);
		int index = findIndex(nums1, nums2, half, start, end + 1);
		int value = getValue(nums1, nums2, index, half - index);
		if (sum % 2 == 1) {
			return value;
		} else {
			int v1 = getValue(nums1, nums2, index + 1, half - index);
			int v2 = getValue(nums1, nums2, index, half - index + 1);
			double re = value + Math.min(v1, v2);
			return re / 2;
		}
	}
}
```