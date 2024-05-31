def F(n):
    print('Computing F('+str(n)+')')
    if n <= 1:
        return n
    else:
        return F(n - 1) + F(n - 2)

print('F(6) = ',F(6))
computation_count = 0
def F(n):
    global computation_count
    computation_count += 1
    if n <= 1:
        return n
    else:
        return F(n - 1) + F(n - 2)
        
computation_count_mem = 0
def F_mem(n):
    if memo[n] != None: # Already computed
        return memo[n]
    else: # Computation needed
        global computation_count_mem
        computation_count_mem += 1
        if n <= 1:
            memo[n] = n
        else:
            memo[n] = F_mem(n - 1) + F_mem(n - 2)
        return memo[n] 

print('F(30) = ',F(30))
print(f'Number of computations: {computation_count}')
print('\nUsing memoization:')
memo = [None]*31
print('F(30) = ',F_mem(30))
print(f'Number of computations with memoiztion: {computation_count_mem}')
def fibonacci_tabulation(n):
    if n == 0: return 0
    elif n == 1: return 1

    F = [0] * (n + 1)
    F[0] = 0 
    F[1] = 1

    for i in range(2, n + 1):
        F[i] = F[i - 1] + F[i - 2]
    
    print(F)
    return F[n]
  
n = 10
result = fibonacci_tabulation(n)
print(f"\nThe {n}th Fibonacci number is {result}")
def nth_fibo(n):
    if n==0: return 0
    if n==1: return 1

    F = [None] * (n + 1)
    F[0] = 0
    F[1] = 1

    for i in range(2, n + 1):
        F[i] = F[i - 1] + F[i - 2]

    return F[n]

n = 6
result = nth_fibo(n)
print(f"The {n}th Fibonacci number is {result}")
def linearSearch(arr, targetVal):
    for i in range(len(arr)):
        if arr[i] == targetVal:
            return i
    return -1

arr = [3, 7, 2, 9, 5]
targetVal = 9

result = linearSearch(arr, targetVal)

if result != -1:
    print("Value",targetVal,"found at index",result)
else:
    print("Value",targetVal,"not found")
    def binarySearch(arr, targetVal):
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == targetVal:
            return mid
        
        if arr[mid] < targetVal:
            left = mid + 1
        else:
            right = mid - 1

    return -1

myArray = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
myTarget = 15

result = binarySearch(myArray, myTarget)

if result != -1:
    print("Value",myTarget,"found at index", result)
else:
    print("Target not found in array.")
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node* next;
} Node;

Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    if (!newNode) {
        printf("Memory allocation failed!\n");
        exit(1);
    }
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

void printList(Node* node) {
    while (node) {
        printf("%d -> ", node->data);
        node = node->next;
    }
    printf("null\n");
}

int main() {
    Node* node1 = createNode(3);
    Node* node2 = createNode(5);
    Node* node3 = createNode(13);
    Node* node4 = createNode(2);

    node1->next = node2;
    node2->next = node3;
    node3->next = node4;

    printList(node1);

    // Free the memory
    free(node1);
    free(node2);
    free(node3);
    free(node4);

    return 0;
}
