# Data Structure

- A **Data Structure** is a particular way of organizing data in a computer so that it can be used effectively. For example, we can store a list of items having the same data-type using the array data structure.
- A **Data Structure** is a named group of data of different data types which can be processed as a single unit. A data structure has well-defined operations, behaviour and properties.

## Array

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

### Selection Sort

The selection sort algorithm sorts an array by repeatedly finding the minimum element (considering ascending order) from unsorted part and putting it at the beginning. The algorithm maintains two subarrays in a given array.

1) The subarray which is already sorted.

2) Remaining subarray which is unsorted.

In every iteration of selection sort, the minimum element (considering ascending order) from the unsorted subarray is picked and moved to the sorted subarray.

**Time Complexity:**

- O(n^2) as there are two nested loops.
- **Auxiliary Space:** O(1)
- The good thing about selection sort is it never makes more than O(n) swaps and can be useful when memory write is a costly operation.

```cpp
#include <bits/stdc++.h>
using namespace std;

void swap(int *x,int *y){
    int temp= *x;
    *x  = *y;
    *y = temp;
}
void selection_sort(int arr[],int n){
    int i,j,min_idx;

    for(int i=0; i<n-1; i++){
        min_idx = i;
        for(j=i+1; j<n ; j++)
            if(arr[j]<arr[min_idx])
                min_idx=j;
        swap(arr[min_idx],arr[i]);
    }
}

void printArray(int arr[], int size)
{
    int i;
    for (i=0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main(){
    int arr[] ={64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);
    cout<<endl<<"Unsorted array - ";
    printArray(arr, n);
    selection_sort(arr,n);
    cout<<endl<<"Sorted array - ";
    printArray(arr, n);
    return 0;
}
```

### Bubble Sort

Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.

**Optimized Implementation:**

- The above function always runs O(n^2) time even if the array is sorted. It can be optimized by stopping the algorithm if inner loop didn’t cause any swap.

```cpp
#include<bits/stdc++.h>
using namespace std;

void swap(int *x,int *y){
    int temp= *x;
    *x  = *y;
    *y = temp;
}
void selection_sort(int arr[],int n){
    int i,j;

    for(int i=0; i<n-1; i++){
        for(j=0; j<n-i-1 ; j++)
            if(arr[j]>arr[j+1])
                swap(arr[j],arr[j+1]);
    }
}

void printArray(int arr[], int size)
{
    int i;
    for (i=0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main(){
    int arr[] ={64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);
    cout<<endl<<"Unsorted array - ";
    printArray(arr, n);
    selection_sort(arr,n);
    cout<<endl<<"Sorted array - ";
    printArray(arr, n);
    return 0;
}
```

### Insertion Sort

Insertion sort is a simple sorting algorithm that works similar to the way you sort playing cards in your hands. The array is virtually split into a sorted and an unsorted part. Values from the unsorted part are picked and placed at the correct position in the sorted part.

- **Time Complexity:** O(n^2)
- **Auxiliary Space:** O(1)

```cpp
#include <bits/stdc++.h>
using namespace std;

void swap(int *x, int *y)
{
    int temp = *x;
    *x = *y;
    *y = temp;
}
void insertion_sort(int arr[], int n)
{
    int i, j, key;
    for (i = 1; i < n; i++)
    {
        key = arr[i];
        j = i - 1;
        while (j >= 0 && arr[j] > key)
        {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}
void printArray(int arr[], int size)
{
    int i;
    for (i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main()
{
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << endl
         << "Unsorted array - ";
    printArray(arr, n);
    insertion_sort(arr, n);
    cout << endl
         << "Sorted array - ";
    printArray(arr, n);
    return 0;
}
```

## Linked List

- It is a linear collection of data elements, called nodes pointing to the node pointing to the next node by means of pointers.
- In simple words, a linked list consists of nodes where each node contains a data field and a reference(link) to the next node in the list.

```cpp
// A linked list node
struct Node {
    int data;
    struct Node* next;
};
Node *ptr;
ptr = new Node;
```

- Code for Linked List :-

    ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    struct Node
    {
        int data;
        struct Node *next;
    };
    Node *head;

    void begin_insert(int item)
    {
        Node *ptr = new Node;
        if (ptr == NULL)
            cout << "\n OVERFLOW!!";
        else
        {
            ptr->data = item;
            ptr->next = head;
            head = ptr;
            cout << "\n Node Inserted";
        }
    }
    void end_insert(int item)
    {
        Node *ptr = new Node;
        Node *temp;
        if (ptr == NULL)
            cout << "OVERFLOW";
        else
        {
            ptr->data = item;
            if (head == NULL)
            {
                ptr->next = NULL;
                head = ptr;
                cout << "\n Node Inserted";
            }
            else
            {
                temp = head;
                while (temp->next != NULL)
                    temp = temp->next;
                temp->next = ptr;
                ptr->next = NULL;
                cout << "\n Node Inserted";
            }
        }
    }
    void specific_insert(int item)
    {
        if (head == NULL)
        {
            cout << "\n no Linked List found ,creating Linkin List....";
            begin_insert(item);
        }
        else
        {
            Node *ptr = new Node;
            Node *temp;
            if (ptr == NULL)
                cout << "OVERFLOW";
            else
            {
                ptr->data = item;
                temp = head;
                int pos;
                cout << "\nEnter position to insert - ";
                cin >> pos;
                for (int i = 1; i < pos; i++)
                {
                    temp = temp->next;
                    if (temp->next == NULL)
                    {
                        cout << "\nCan't Insert";
                        return;
                    }
                }
                ptr->next = temp->next;
                temp->next = ptr;
                cout << "\n Node Inserted";
            }
        }
    }
    void begin_del()
    {

        if (head == NULL)
            cout << "\n List is empty";
        else
        {
            Node *ptr = head;
            head = ptr->next;
            free(ptr);
            cout << "\n Node deleted at the beginning of the linked List";
        }
    }
    void end_del()
    {
        if (head == NULL)
            cout << "\n List is empty";
        else if (head->next == NULL)
        {
            head = NULL;
            free(head);
            cout << "\n Only Node deleted of the linked List";
        }
        else
        {
            Node *ptr1, *ptr = head;
            while (ptr->next != NULL)
            {
                ptr1 = ptr;
                ptr = ptr->next;
            }
            ptr1->next = NULL;
            free(ptr);
            cout << "\n Node deleted at the beginning of the linked List";
        }
    }
    void specific_del()
    {
        if (head == NULL)
            cout << "\n List is empty";
        else
        {
            Node *ptr = head;
            Node *ptr1;
            int pos;
            cout << "\nEnter position to delete - ";
            cin >> pos;
            for (int i = 1; i <= pos; i++)
            {
                ptr1 = ptr;
                ptr = ptr->next;
                if (ptr == NULL)
                {
                    cout << "\ncan't delete";
                    return;
                }
            }
            ptr1->next = ptr->next;
            free(ptr);
            cout << "\n Node Deleted";
        }
    }
    void search(int item)
    {
        Node *ptr = head;
        int flag = 1;
        if (ptr == NULL)
            cout << "\n List is Empty";
        else
        {
            for (int i = 1; ptr != NULL; i++, ptr = ptr->next)
            {
                if (ptr->data == item)
                {
                    flag = 0;
                    cout << "\nItem Found at Location " << i;
                }
            }
            if (flag == 1)
                cout << "\nItem Not Found!!";
        }
    }
    void display()
    {
        Node *i = head;
        cout << endl
             << "Linked List - ";
        while (i != NULL)
        {
            cout << "  " << i->data;
            i = i->next;
        }
    }
    int main()
    {
        int option, item;
        do
        {
            cout << "\n0.Exit.";
            cout << "\n1.To Insert at the beginning of Linked List";
            cout << "\n2.To Insert at the End of Linked List";
            cout << "\n3.To Insert after specified Node in Linked List";
            cout << "\n4.To Delete at the beginning of Linked List";
            cout << "\n5.To Delete at the End of Linked List";
            cout << "\n6.To Delete after specified Node in Linked List";
            cout << "\n7.To search";
            cout << "\n Enter option - ";
            cin >> option;
            switch (option)
            {
            case 0:
                cout << "\nExiting.......";
                break;
            case 1:
                cout << "\nEnter data to insert - ";
                cin >> item;
                begin_insert(item);
                display();
                break;
            case 2:
                cout << "\nEnter data to insert - ";
                cin >> item;
                end_insert(item);
                display();
                break;
            case 3:
                cout << "\nEnter data to insert - ";
                cin >> item;
                specific_insert(item);
                display();
                break;
            case 4:
                begin_del();
                display();
                break;
            case 5:
                end_del();
                display();
                break;
            case 6:
                specific_del();
                display();
                break;
            case 7:
                cout << "\nEnter data to search - ";
                cin >> item;
                search(item);
                break;
            default:
                cout << "\nInvalid Option";
                break;
            }
        } while (option != 0);
        display();
    }
    ```

##
