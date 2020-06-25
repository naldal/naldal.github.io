---

title: 합병정렬(Merge Sort)이란 무엇인가

categories:

- algorithm
- sort

---

<br><br>
![]({{ site.url }}{{ site.baseurl }}/assets/images/mergesort.gif){: .align-center}
<br><br>

## 합병정렬 알고리즘 요약

합병 정렬은 일반적인 방법으로 구현했을 때 **안정 정렬**에 속하며, 분할 정복 알고리즘 중 하나이다.

- 분할 정복(divide and conquer) 방법
    - 문제를 작은 2개의 문제로 분리하고 각각을 해결한 다음, 결과를 모아서 원래의 문제를 해결하는 전략이다.
    - 분할 정복 방법은 대개 순환 호출을 이용하여 구현한다.
- 과정 설명
    1. 리스트의 길이가 0 또는 1이면 이미 정렬된 것으로 본다. 그렇지 않을 경우에는
    2. 정렬되지 않는 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다
    3. 각 부분 리스트를 재귀적으로 합병 정렬을 이용해 정렬한다.
    4. 두 부분 리스트를 다시 하나의 정렬된 리스트로 합병한다.

## 합병 정렬의 과정

- 하나의 리스트를 두 개의 균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 방법이다.
- 합병 정렬은 다음의 단계들로 이루어진다.
    - 분할(Divide): 입력 배열을 같은 크기의 2개의 부분 배열로 분할한다.
    - 정복(Conquer): 부분 배열을 정렬한다. 부분 배열의 크기가 충분히 작지 않으면 **순환 호출**을 이용하여 다시 분할 정복 방법을 적용한다.
    - 결합(Combine): 정렬된 부분 배열들을 하나의 배열에 합병한다.

<br><br>
![]({{ site.url }}{{ site.baseurl }}/assets/images/merge-sort-concepts.png){: .align-center}
<br><br>

## 합병 정렬 알고리즘 예제

```jsx
public class MergeSort {
    static int[] tmp;
    public static void main(String[] args) {
        int[] arr = new int[]{1, 9, 8, 5, 2, 3, 7, 6};
        tmp = new int[arr.length];
        mergeSort(arr, 0, arr.length-1);
        System.out.println(Arrays.toString(arr));

    }

    private static void mergeSort(int[] arr, int left, int right) {
        int mid;

        if (left < right) {
            mid = (left+right)/2;
            mergeSort(arr, left, mid);
            mergeSort(arr, mid+1, right);
            merge(arr, left, mid, right);
        }
    }

    private static void merge(int[] arr, int left, int mid, int right) {
        int i , j, k, l;
        // i: 정렬된 왼쪽 리스트에 대한 인덱스
        // j: 정렬된 오른쪽 리스트에 대한 인덱스
        // k: 정렬될 리스트에 대한 인덱스
        i=left;
        j=mid+1;
        k=left;

        while (i<=mid && j<= right) {
            if (arr[i]<=arr[j]) {
                tmp[k++] = arr[i++];
            } else {
                tmp[k++] = arr[j++];
            }
        }

        if (i>mid) {
            for (l=j; l<=right; l++) {
                tmp[k++] = arr[l];
            }
        } else {
            for (l=i; l<=mid; l++) {
                tmp[k++] = arr[l];
            }
        }

        for (l=left; l<=right; l++) {
            arr[l] = tmp[l];
        }
    }
}
```
