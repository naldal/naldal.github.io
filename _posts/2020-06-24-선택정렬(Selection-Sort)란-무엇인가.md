---

title: 선택정렬(Selection Sort)이란 무엇인가

categories:

- algorithm
- sort

---

<br><br>
![]({{ site.url }}{{ site.baseurl }}/assets/images/insertion.gif){: .align-center}
<br><br>

선택정렬은 첫 번째 자료를 두 번째 자료부터 마지막 자료까지 차례대로 비교하여 가장 작은 값을 찾아 첫 번째에 놓고, 두 번째 자료를 세 번째 자료부터 마지막 자료까지와 차례대로 비교하여 그 중 가장 작은 값을 찾아 두 번째 위치에 놓는 과정을 반복하여 정렬을 수행하는 정렬 알고리즘이다.

**소스코드**

```jsx
public static void main(String[] args) {
        int[] arr = {3, 6, 2, 8, 1, 15, 11, 5};
        selectionSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    private static void selectionSort(int[] arr) {
        for (int i=0; i<arr.length; i++) {
            int min = i;
            for (int j=1+i; j<arr.length; j++) {
                if (arr[j] < arr[min]){
                    min = j;
                }
            }
            swapper(arr, min, i);
        }
    }

    private static void swapper(int[] arr, int min, int i) {
        int tempnum = arr[min];
        arr[min] = arr[i];
        arr[i] = tempnum;
    }
```

<br><br>

선택정렬을 구현하고 있는 selectionSort 함수를 살펴보자.

```jsx
private static void selectionSort(int[] arr) {
        for (int i=0; i<arr.length; i++) {
            int min = i;
            for (int j=1+i; j<arr.length; j++) {
                if (arr[j] < arr[min]){
                    min = j;
                }
            }
            swapper(arr, min, i);
        }
    }
```

정렬할 배열을 인자로 받아 정렬을 실행한다.

순회할 때마다 기준 인덱스를 하나씩 높이는데 이때 기준 인덱스를 변수 `min`에 할당한다.

이후 기준값을 나머지 비교값들과 하나씩 비교하여 비교값들 중 가장 작은 값이 들어있는 인덱스 `j`를 `min`에 대입한다. 

마지막으로`swapper(arr, min, i)` 함수를 통해 `min` 과 기준값인 `i` 의 값을 바꿔주면 된다.

<br><br><br>
![]({{ site.url }}{{ site.baseurl }}/assets/images/likeplz.gif)<br><br>
좋아요와 댓글은 포스팅에 큰 힘이 됩니다!
