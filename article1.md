# Obtain index from pointers in C++

<p>Well I encountered this problem when I was practicing my DSA, so here I will share how its stored in my mind. In this article we will look at how to compute the index using pointers returned by STL functions. It will be explained in such a way that even a 4th grader would get it.</p>

**Table of contents**
1. Introduction
2. Problem statement
3. Reason for this behavior
4. How to solve this issue?
    4.1	Solution 1 (Subtracting the starting iterator)
    4.2	Solution 2 (Using std::distance())
5. Implementing the solutions
6. Time & Space Complexity

## 1. Introduction 
So I think you have an idea on what a pointer and STL functions are. If not don’t worry, I gotcha!
<p>Pointers have confusing definitions online, so let’s put it this way pointers are variables whose value is the address of another variable. It has various use cases but it’s enough for now. On the other hand Standard Template Library (STL) functions are instances of the classes present in it.</p>
<p>Since we have the basics covered, lets move on to the problem statement.</p>
   
## 2. Problem Statement
<p>The given problem statement is to compute the index using pointers returned by STL functions, lets understand it through an example.</p>

### Example:
<p>In the following code we are finding the minimum element in a vector using std::min_element( start, end ). This is an STL function which returns a pointer, pointing to the minimum element in the vector.</p>

```
// Program to find the minimum element in a vector
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;
int main()
{
    // Initialising a vector
    vector<int> v = {15, 51, 5, 12, 70, 102};

    // min_element(start,end); 
    //is an stl function which returns a pointer
    // pointing the minimum element in the vector
    // * Symbol is used to get the value pointed by the pointer
    cout << "Min element is:" << *min_element(v.begin(), v.end()) << endl;

    // Printig the index of the minimum element
    cout << "Index is: ";
    printf("%d", min_element(v.begin(), v.end()));

    return 0;
}
```
Output:
  ```
    Min element is:5
    Index is: 16717912
  ```
Woah! What happened! We are we getting a random value as the index. But why?
##3. Reason for this behavior
<p>We can observe that the value is different each time we run it. So, is it a random value?</p>
<p>The answer is NO! Reason for this behavior is very simple, remember the definition of pointers?</p> 
<p>The number getting printed is the address of that memory location where that number is stored. It changes each time we run because the vector is getting initialized for each run. So how to solve this?</p>
    
## 4. How to solve this issue?
To solve this issue and to obtain the index we have two ways those are: 
* To subtract the starting iterator and 
* To use an STL function 

### 4.1 Solution 1 (Subtracting the starting iterator)
Lets take the same example as before and while printing the index lets subtract the starting iterator.
   ```
// Program to find the minimum element in a vector
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;
int main()
{
    // Initialising a vector
    vector<int> v = {15, 51, 5, 12, 70, 102};

    // min_element(start,end); is an stl function which returns a pointer
    // pointing the minimum element in the vector
    // * Symbol is used to get the value pointed by the pointer
    cout << "Min element is:" << *min_element(v.begin(), v.end()) << endl;

    // Printig the index of the minimum element 
    //by subtracting the staring iterator
    cout << "Index is: ";
    printf("%d", min_element(v.begin(), v.end()) - v.begin());

    return 0;
}
   ```
Output:
  ```
    Min element is:5
    Index is: 2
  ```
    
<p>Vola! We got the correct index. But how did this happen. The main reason is because the ==vector space is continuous==. </p>
Lets demonstrate it with code.

 ```
 // Program to find the minimum element in a vector
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;
int main()
{
    // Initialising a vector
    vector<int> v = {15, 51, 5, 12, 70, 102};

    // min_element(start,end); is an stl function which 
    //returns a pointer
    // pointing the minimum element in the vector
    // * Symbol is used to get the value pointed by the pointer
    cout << "Min element is:" << *min_element(v.begin(), v.end()) << endl;

    // Printing the memory address of index 2
    cout << "Memory address of the minimum element is: ";
    printf("%d\n", min_element(v.begin(), v.end()));

    // Printing the memory address of index 0
    cout << "Memory address of the starting element is: ";
    printf("%d\n", v.begin());

    // Printig the index of the minimum element 
    //by subtracting the staring iterator
    cout << "Index is: ";
    printf("%d", min_element(v.begin(), v.end()) - v.begin());

    return 0;
}
   ```
   Output:
  ```
   Min element is:5
   Memory address of the minimum element is: 15276120
   Memory address of the starting element is: 15276112
   Index is: 2
  ``` 
  Calculation
   ```
    Value of desired location  = 15276120
    Value of starting iterator = 15276112
    Value after subtracting = 8
    Number of bytes occupied by int = 4
    	=> 8 / 4 = 2, The index of the minimum element.
   ```
This is how we are getting the index value after subtracting the starting iterator.

### 4.2 Solution 2 (Using std::distance())
    
 <p>std::distance() is an STL function and it is used when we have to find the number of elements between two iterators. It returns number of elements as integer.</p>
    
   ```
    // Program to find the minimum element in a vector
#include <iostream>
#include <algorithm>
#include <vector>
#include <iterator>

using namespace std;
int main()
{
    // Initialising a vector
    vector<int> v = {15, 51, 5, 12, 70, 102};

    // min_element(start,end); is an stl function 
    //which returns a pointer
    // pointing the minimum element in the vector
    // * Symbol is used to get the value pointed by the pointer
    cout << "Min element is:" << *min_element(v.begin(), v.end()) << endl;

    // Printig the index of the minimum element using distance()
    cout << "Index is: ";
    cout << distance(v.begin(), min_element(v.begin(), v.end()));

    return 0;
}
 ```
 
 Output:
  ```
   Min element is:5
   Index is: 2
  ``` 
  
This function belong to the `<iterator>` header file.

## 5. Implementing the solutions
Lets apply the knowledge we gained to find an element in a vector.
Here we will be using std::find().

```
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    // Initializing the vector
    vector<int> v = {7, 50, 45, 106, 76, 10, 3, 67, 33, 15, 0};

    // value to be found
    int toFind = 10;

    // assigning the pointer with the return value
    auto it = find(v.begin(), v.end(), toFind);

    // If the element not present
    if (it == v.end())
    {
        cout << "Element is not present" << endl;
    }
    else
    {
        // Doing our calculation
        int idx = it - v.begin();

        // Using the distance function
        // int idx = distance(v.begin(), it);

        cout << "Index is: " << idx << endl;
    }

    return 0;
}
```
Output:
```
Index is: 5
```

## 6. Time & Space Complexity
* In solution 1 we are using std::min_element() function which is a part of STL library. 
Time Complexity: O(n) Where n is the size of vector.
Space Complexity: O(1) As no extra space is being consumed.

* In solution 2 we are using both std::min_element(), std::distance() function which are a part of STL library.
Time Complexity: O(n) Where n is the size of vector.
Space Complexity: O(1) As no extra space is being consumed
* Code under implementing solution uses std::find() function which is a part of STL library
Time Complexity: O(log(n)) Where n is the size of vector.
Space Complexity: O(1) As no extra space is being consumed

<p>By the end of this article you must have complete idea on how to compute the index using pointers returned by STL functions. Lets test your knowledge</p>

<div class="container"style="width:100%;">
<h2>Question</h2>
<h4>Which of the following does not return pointer?</h4>
<h6 id="question_message" class="question_message"></h6>
<section class="questionlist">
<div class="correct_option">std::distance()</div>
<div class="wrong_option">std::min_element()</div>
<div class="wrong_option">std::find()</div>
<div class="wrong_option">vector::begin()</div>
</section>
<div class="Answer_explanation">
    <br><br>
   std::distance() is the correct answer. It returns the number of elements between two iterators.
</div>
</div>
