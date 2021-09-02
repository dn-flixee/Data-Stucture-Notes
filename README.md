
# Data Structure


- A **Data Structure** is a particular way of organizing data in a computer so that it can be used effectively. For example, we can store a list of items having the same data-type using the array data structure.
- A **Data Structure** is a named group of data of different data types which can be processed as a single unit. A data structure has well-defined operations, behaviour and properties.

## Array

---

- It is a collection of similar data items stored at contiguous memory locations and elements can be accessed randomly using indices of an array.
- Example :-

```cpp
int arr[5] = {1,2,3,4,5};
```

### Basic Operation on 1D Array :-

- **Insertion**

    ```cpp
    #include<iostream>
    using namespace std;

    int* insert(int arr[],int &n,int pos,int x){

        for(int i=n; i>=pos; i--){
            arr[i]=arr[i-1];
        }
        arr[pos - 1] = x;

        return arr;
    }

    int main(){
        int i,arr[11]= {0},n=10;

        for(i = 0 ; i< 10 ; i++){
            arr[i] = i + 1 ;
            cout<<" "<<arr[i];
        }
        cout << endl;

        int x = 50,pos=5;

        insert(arr,n,pos,x) ;   

        for (i = 0; i < n + 1; i++)
            cout << arr[i] << " ";
        cout << endl;
    }
    ```

- Deletion

    ```cpp
    #include<iostream>
    using namespace std;

    int del(int arr[],int &n,int x){
        int i;
        for(i = 0; i < n ; i++)
            if(arr[i]==x)
                break;
        
        if(i<n){
            n--;
            for(int j = i ; j<n;j++)
                arr[j]=arr[j+1];
        }
        return n;
    }

    int main(){
        int i,arr[10]= {0},n=10;

        for(i = 0 ; i< 10 ; i++){
            arr[i] = i + 1 ;
            cout<<" "<<arr[i];
        }
        cout << endl;

        int x = 5;

        n = del(arr,n,x) ;   

        for (i = 0; i < n ; i++)
            cout << arr[i] << " ";
        cout << endl;
    }
    ```

## Sorting

---

### Selection Sort

The selection sort algorithm sorts an array by repeatedly finding the minimum element (considering ascending order) from unsorted part and putting it at the beginning. The algorithm maintains two subarrays in a given array.

1) The subarray which is already sorted.

2) Remaining subarray which is unsorted.

In every iteration of selection sort, the minimum element (considering ascending order) from the unsorted subarray is picked and moved to the sorted subarray.
