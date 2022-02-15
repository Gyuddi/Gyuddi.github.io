---
title:  "Radix Sort"
excerpt: "기수 정렬을 자바에서 araboja"

categories:
  - Backjoon
tags:
  - [sorting, algorithm, radix sort, merge sort]

toc: true
toc_sticky: true
 
date: 2022-02-10
last_modified_at: 2022-02-10
---
합병정렬의 시간 복잡도는 O(NlogN)   
기수정렬의 시간 복잡도는 O(N)이지만, 추가적인 데이터를 굉장히 많이 필요로한다.   
사실상 카운팅 정렬과 함께 시간 복잡도가 가장 낮은 정렬 알고리즘이다.   
기수정렬 파이썬으로 구현할때는 정말 쉬웠는데 자바는 어렵따.         
*Q10989.class*
```java
public class Q10989 {
    public static void main(String[] args)throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int total = Integer.parseInt(br.readLine());
        int[] arr = new int[total];
        for (int i = 0; i < total; i++) {
            arr[i] = Integer.parseInt(br.readLine());
        }
        radixsort(arr);
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        for (int a:arr){
            bw.write(a+"\n");
        }
        bw.flush();
        bw.close();
    }
    //가장 큰 값 호출
    public static int getMax(int[] arr){
        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if(arr[i]>max){
                max = arr[i];
            }
        }
        return max;
    }
    //각 자릿수별 정렬
    public static void countSort(int[] data, int exp) {
        int[] output = new int[data.length];
        //자릿수 카운트
        int[] count = new int[10];

        for(int i=0; i<data.length; i++) {
            count[(data[i]/exp)%10]++;
        }
        //누적으로 카운트를 쌓아 그 순서를 나타낸다.
        for(int i=1; i<10; i++) {
            count[i] += count[i-1];
        }
        //data의 값을 count와 비교하여 순서를 획득,그 순서를 기준으로   output에 재정렬
        for(int i=data.length-1; i>=0; i--) {
            output[count[(data[i]/exp%10)]-1] = data[i];
            //중복 위험을 피하기위해
            count[(data[i]/exp)%10]--;
        }

        for(int i=0; i<data.length; i++) {
            data[i] = output[i];
        }
    }
    //자릿수 조절.
    public static void radixsort(int[] data) {
        int m = getMax(data);
        for(int exp=1; m/exp>0; exp*=10) {
            countSort(data, exp);
        }
    }
}
```
끝!
