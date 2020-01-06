# Algorithms

## Searching Algorithms

### Linear Search 

Definition: Linear search (also as known as sequential search) is the process of finding a value by searching through every element till we find the value that we want.

![Linear-Search](https://user-images.githubusercontent.com/42160652/71761075-d57d0800-2e94-11ea-88b9-98264291afa3.png)
###### It goes through each element till we found the target.

**Linear Search Implementation in Java**
```java
public int linearSearch(int a[], int target){

//returns the index of the target 
for(int x=0; x<a.length; x++){
if(a[x] == target)
      return x;
 }
 
 //returns -1 if the element is not found
 return -1;
}
```

**Time Complexity:** The time complexity of this prorgram is O(n) because it will take a very short time to find the first
element but then finding the next element will take longer and so on. The time it takes to find each element will increase linearly which is why the time complexity is O(n).

__Best Case, Average Case, and Worst Case__ 

**Best Case:** You found the first element                           
      
     Big O Notation: O(1)

**Average Case:** You found the middle element
     
     Big O Notation: O(n), even though it is O(n/2) but remember we will drop the constant which is 1/2

**Worst Case:** You found the last element or element is not found
     
     Big O Notation: O(log n)
   
###### Note: n is the length of the line
      
### Binary Search 

Definition: Binary search (also as known as half-interval search) is used to find a specific value within an array by cutting half of an array.

![Binary Search](https://www.geeksforgeeks.org/wp-content/uploads/Binary-Search.png)
###### Since our middle element is 16 and we want to find 23, we can get rid of all of the elements that comes before 16 and 16 itself. Then we find the middle element between 23 and 91. Since 23 comes before 56, we can remove 56 and every element that comes after 56. With 23 and 28 left, 23 is our middle element and we have found it.
###### REMEMBER AN ARRAY MUST BE SORTED IN ORDER TO DO BINARY SEARCH.

**Binary Search Implementation in Java**
```java
public static int binarySearch (int[] arr, int from, int to, int target) {

if (from > to) {
  
   return -1; //val not found 

}
  
int mid = (from + to)/2;

if (arr[mid] == target){

   return mid;

}else if (target > arr[mid]){
   
   return binSearch(arr,mid+1,to,target);

}else{

   return binSearch(arr,from,mid-1,target);

      }

}
```

**Time Complexity:** The time complexity of this prorgram is O(log n) since we are dividing the length of the line and getting rid of the half that surely does not contain the value. We keep on doing this until our line is just empty. A line with a length of 8 will cut the line at most 3 times since log 8 is 3. Remember our base of the log is 2 so 2^3 is 8. For more information about the log n runtime click [here](https://github.com/fayedraza/Big-O#olog-n-runtime).

__Best Case and Worst Case__

**Best Case:** We found the element by first comparison

     Big O Notation: O(1)

**Worst Case:** We found the element by last comparison or element was not found at all

    Big O Notation: O(n)
    
## Sorting Algorithms

### Selection Sort

Definition: Selection sort is a sorting algorithm that sorts an array by repeatedly finding the minimum value and placing it to the beginning of the array until the array is sorted.

![1*S-wdMkkaX3Gr4bQrbqu_1Q](https://user-images.githubusercontent.com/42160652/71804432-6d175d80-3031-11ea-8f6f-6416142d2ec6.jpeg)

###### This is an example of selection sort where we repatedly bring the minimum element to the front until the array is sorted.

**Selection Sort Implementation in Java**
```java
public static void sort(int[] a) { 
        int n = a.length;
      for (int i = 0; i < n; i++) {
           int min = i;
          for (int j = i+1; j < n; j++) {
              if (a[j] < a[min]) 
                    min = j;
          }
         int tmp = a[i]; 
         a[i] = a[min]; 
         a[min]= tmp;
      } 
}
```

**Time Complexity:** The time complexity of this prorgram is O(n^2) since it is a nested for loop where the input, n, is our array.

__Best Case and Worst Case__

**Best Case:** Best case applies to an array that is already sorted from the least to the greatest. We still go each element for every array run which is why the runtime is still O(n^2).

    Big O Notation: O(n^2)

**Worst Case:** Worst case applies to an array that goes from the greatest value to the least value. 

    Big O Notation: O(n^2)
