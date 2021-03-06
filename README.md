# Algorithms

## Searching Algorithms

### Linear Search 

Definition: Linear search (also as known as sequential search) is the process of finding a value by searching through every element till we find the value that we want.

![IMG_2588](https://user-images.githubusercontent.com/42160652/72125591-1f536b80-3337-11ea-9106-afcba7d31d94.jpeg)

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

![IMG_2592](https://user-images.githubusercontent.com/42160652/72124651-8bcc6b80-3333-11ea-92aa-4d5050637c26.jpeg)
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

### Insertion Sort

Defintion: Insertion sort is a sorting algorithm that builds an element one item at a time.

![IMG_2568](https://user-images.githubusercontent.com/42160652/72004940-79aada00-321a-11ea-8424-85c1badc9cf3.jpeg)

###### Each element is moved to the sorted part. 

**Insertion Sort Implementation in Java**
```java
public static void insertion2(int[] a){ 

   int n = a.length;
   for (int i = 1; i < n; i++){
   
       for (int j = i; j > 0; j--){
       
          if(a[j-1] > a[j]){
          
           int temp = a[j-1];  
           a[j-1] = a[j];  
           a[j] = temp;
           
          }else {
          
            break;
            
          }
            
        } 
        
    }
    
}
```

**Time Complexity:** The time complexity of this prorgram is O(n^2) since it is a nested for loop where the input, n, is our array.

__Best Case and Worst Case__

**Best Case:** Best case applies to an array that is already sorted from the least to the greatest. In this case, we will traverse through the array which is why the runtime is O(n).

    Big O Notation: O(n)

**Worst Case:** Worst case applies to an array that goes from the greatest value to the least value. 

    Big O Notation: O(n^2)

### Selection Sort

Definition: Selection sort is a sorting algorithm that sorts an array by repeatedly finding the minimum value and placing it to the beginning of the array until the array is sorted.

![IMG_2642](https://user-images.githubusercontent.com/42160652/72944101-f4f5ab00-3d45-11ea-9fd1-61cc6c89b5c2.jpeg)

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

**Best Case:** Best case applies to an array that is already sorted from the least to the greatest. We still go through each element for every array run which is why the runtime is still O(n^2).

    Big O Notation: O(n^2)

**Worst Case:** Worst case applies to an array that goes from the greatest value to the least value. 

    Big O Notation: O(n^2)
    
### Merge Sort

Definition: Merge sort is a storting algorithm which consists of dividing the elements and bringing back the elments to a sorted group of elements.

![IMG_2594](https://user-images.githubusercontent.com/42160652/72125506-e0251a80-3336-11ea-81f0-1eeffd29b923.jpeg)

###### This is an example of merge sort. As you can see, we first divide the elements till they are alone. After that they will be combined till all of the elements have been sorted. 
 
 **Selection Sort Implementation in Java**
```java
public static void sort (int[] a, int lo, int hi){
   
   int n = hi - lo;   
  
    if ( n <= 1 ) 
        return;  
 
  int middle = lo + n/2;
    
  sort(a, lo, middle);   
  sort(a, middle, hi);   
  merge(a, lo, middle, hi); 
   
}
     
public static void merge (int[] a, int lo, int mid, int hi){
    
     int i =  lo, j = mid, n = hi - lo;
     int[] aux = new aux[n];   
     
     for (int k = 0; k < n; k++) {     
       
        if (i == mid) 
            aux[k] = a[j++];   
        else if (j == hi) 
            aux[k] = a[i++];     
        else if (a[j] < a[i]) 
            aux[k] = a[j++];
        else 
            aux[k] = a[i++];
        
        }
        
  ```
 
**Time Complexity:** The time complexity of this prorgram is O(nlog n) since n items are iterated log n times.

__Best Case and Worst Case__

**Best Case:** Even if the array is sorted, it will still divide and conqueror.

    Big O Notation: O(nlog n)

**Worst Case:** It will apply to an arrary that goes from the greatest to the least which consists of divide and conqueror.

    Big O Notation: O(nlog n)
 
