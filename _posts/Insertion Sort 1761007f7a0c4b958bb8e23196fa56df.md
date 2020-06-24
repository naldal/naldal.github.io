# 삽입정렬(Insertion Sort)이란 무엇인가

![Insertion%20Sort%201761007f7a0c4b958bb8e23196fa56df/insertion.gif](Insertion%20Sort%201761007f7a0c4b958bb8e23196fa56df/insertion.gif)

삽입정렬은 1부터(0아님) n까지 순서대로 index를 설정하여 현재위치보다 앞쪽을 순회하여, 기준 index값보다 큰 값들을 한칸씩 뒤쪽으로 밀고 기준 index보다 작은 값을 만나면 해당 위치에 삽입(insertion)하는 정렬알고리즘이다.

구현하기 까다롭지 않은 알고리즘이지만...

It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort. 

퀵 정렬, 힙 정렬, 마지 정렬과 같은 고급알고리즘에서 훨씬 효율적이지 못하다는 단점을 가지고 있다.

More efficient in practice than most other simple quadratic (i.e., O(n2)) algorithms such as selection sort or bubble sort

하지만 실지로 선택정렬이나 버블소트보다 더 효율적이다. 

구현코드는 다음과 같다.

```jsx
		public static void main(String[] args) {
        int[] arr = {9, 1, 15, 4, 7, 5};
        insertionSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    private static void insertionSort(int[] arr) {
        for (int i=1; i<arr.length; i++) {
            int standard = arr[i];
            int aux = i-1;
            while (aux >= 0 && arr[aux] > standard) {
                arr[aux+1] = arr[aux];
                aux--;
            }
            arr[aux+1] = standard;
        }
    }
```

insertionSort 함수를 살펴보겠다.

```jsx
 private static void insertionSort(int[] arr) {
        for (int i=1; i<arr.length; i++) {
            int standard = arr[i];
            int aux = i-1;
```

정렬할 배열을 인자로 받아 삽입정렬을 실행한다.

인덱스 1부터 마지막 인덱스까지 순회하는 정렬이므로, 기준값(standard)을 배열의 두 번째 인덱스(arr[1])로 세우고, 비교값(aux)를 기준값보다 하나 아래로 설정(i-1)한다.

```jsx
 while (aux >= 0 && arr[aux] > standard) {
                arr[aux+1] = arr[aux];
                aux--;
       }
```

기준값이 아래 인덱스로 순회하면서 자신보다 큰 값을 찾으면 해당 값을 오른쪽으로 한칸씩 민다. 이때 조건은

1. 비교값이 인덱스 0 이상일 것. (aux ≥ 0)
2. 비교값이 기준값보다 클 것. (arr[aux] > standard)

이 과정을 마치고 나면 저장해 두었던 기준값을 마지막으로 정렬했던 인덱스 앞으로 삽입해야 한다. 

aux—; 으로 순회하기 때문에 while문 탈출 시 aux는삽입해야 할 인덱스보다 한칸 앞의 인덱스를 가리키고 있다. 

```jsx
  arr[aux+1] = standard;
```

때문에 aux+1 인덱스 자리에 기준값을 넣어주면 정렬이 완료된다.

댓글은 포스팅에 큰 힘이 됩니다!