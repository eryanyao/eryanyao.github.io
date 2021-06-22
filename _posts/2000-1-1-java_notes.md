---
layout: post
title: JAVA Note
---

Below is my JAVA note for preparing my interview.
<br><br>
### input, output
```java
package name
import java.util.*

public class Name{
  public static void main(String args[]){
    //output
    System.out.print("Hello World"); 
    
    //input
    Scanner keyboard = new Scanner(System.in);
    String text = keyboard.nextLine(); 
  }
}
```

### if...else
```java
if(condition==true){
  
}
else{ //condition==false

}
```
### for loop
```java
for(int i=0;i<10;i++){
  System.out.print(i);
}
```
### try...catch
```java
```

## Question
1. question from <https://app.codility.com/demo/take-sample-test/>

Write a function:\
class Solution { public int solution(int[] A); }\
that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.\
For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.\
Given A = [1, 2, 3], the function should return 4.\
Given A = [−1, −3], the function should return 1.\
Write an efficient algorithm for the following assumptions:\
N is an integer within the range [1..100,000];\
each element of array A is an integer within the range [−1,000,000..1,000,000].

```java
import java.util.*;

class Solution {
    public int solution(int[] A) {  
        int minInt = 1; 
        int length = A.length; 
        Arrays.sort(A);   
        
        for (int i=0; i<length; i++){
            if(A[i] == min){
                min++;
            }
        }   
        return min;    
    }
}
```

```java

import java.util.*;

class Solution {
    public int solution(int N) {
        // write your code in Java SE 8
        String binary = Integer.toBinaryString(N);
		int compte = 0, comptegap = 0, result = 0;
		char[] value = binary.toCharArray();
		System.out.print(value);

		for (char v : value) {
			if (v == '1') {
				compte++;
			}

			if (v == '0') {

				if (compte == 2) {

					if (result < comptegap) {
						result = comptegap;
					}

					comptegap = 0;
				} else {
					result = 0;
				}

				comptegap++;
			}
		}
		return result;
    }
}
```
