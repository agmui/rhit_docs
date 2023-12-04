---
weight: 111
title: "C++ basics"
description: ""
icon: "article"
date: "2023-12-03T20:24:17-05:00"
lastmod: "2023-12-03T20:24:17-05:00"
draft: false
toc: true
---

Great resource [w3schools](https://www.w3schools.com/cpp/default.asp)

### Variables
```cpp
int x = 0;
float f = 1.0;
string greeting = "Hello"; 
char character = 'a';
```

### Comments
```cpp
// one line comment

/*
multi line comment
another line
yet another line!!
*/
```

### Print
```cpp
std::cout << "hello world" << std::endl;

// or 

printf("hello world\n"); // the \n means newline
```

### If
```cpp

int never_gona = 0;
if(never_gona){
    printf("give you up\n");
}

// else if
int amount_of_pilk = 10;
if(amount_of_pilk == 0){
    printf("sad\n");
} else if (amount_of_pilk < 10) {
    printf("it is wut it is\n");
} else{
    printf("LEZZ GOOO\n");
}

```

### Loops
```cpp
for(int i=0; i<10; i++){
    printf("%d\n",i); // %d means digit so we are printing the digit i
}
// outputs:
// 0
// 1
// 2
// 3
// ...

int j = 0;
while(j < 3){
    printf("%d\n",j);
    j++;// increments j
}
// outputs:
// 0
// 1
// 2
```


### Array
```cpp
int[] arr = {1, 2, 3};
printf("%d\n", arr[0]); // prints 1

arr[0] = 69;
printf("%d\n", arr[0]); // prints 69
```

### Functions
```cpp
int addOne(int x){ // just adds one to x
    x++;
    return x;
}

int myNum = 0;
int output = addOne(myNum);
printf("%d\n", output);
```