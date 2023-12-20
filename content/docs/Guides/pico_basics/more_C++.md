---
weight: 119
title: "More_C++"
description: ""
icon: "article"
date: "2023-12-03T21:00:30-05:00"
lastmod: "2023-12-03T21:00:30-05:00"
draft: false
toc: true
---

### IceCream

### include/define
like python or Java `import`  

Ilk.h:
```cpp
class Ilk{
    ...
}
```
main.cpp
```cpp
#include "Ilk.h" // like Ctrl+C and Ctrl+V

#define PIN_NUM 10 // like find and replace
...
int main(){
    int newPinNum = PIN_NUM+2;
}
```
output:

```cpp
class Ilk{
    ...
}

...

int main(){
    int newPinNum = 10+2;
}
```

### Header guards
```cpp
#ifndef PICO_DRIVERS_H_
#define PICO_DRIVERS_H_
...
#endif //  PICO_DRIVERS_H_
```

### Pointers

#### Pass by ref

### Arrays(and getting array length)

### Namespaces

```cpp
std::string myStr = "normal";
```

```cpp
using namespace std;

string myStr = "with using keyword";
```

```cpp
namespace std{
    string myStr = "with brackets";
    // ...
}
```

namespaces with class example:

```cpp FIXME: check if it is correct
namespace showUp{
    class Jason{
        ...
    }
}
...
int main(){
    showUp::Jason();
}
```

### Classes

```cpp
#include <iostream>
#include <string>

using namespace std;

class Ilk
{
private:
    int milk;
    int private_func() {
        return 69;
    }
public:
    Ilk(int milk) {
        this->milk = milk;
    }
    ~Ilk() {}
    void drink(int galOfPilk) {
        printf("drinking %dL of PILK\n", galOfPilk);
        printf("%d\n", this->private_func());
    }
    int getMilk() {
        return this->milk;
    }
};
class Pilk : public Ilk
{
private:
    string cola;
    int numDrinks;
public:
    Pilk(string cola, int numDrinks, int milk)
        : cola(cola),
          numDrinks(numDrinks),
          Ilk(milk)
    {
        printf("pilk\n");
    }
    string getCola() {
        return cola;
    }
};

int main()
{
    Ilk *i = new Ilk(420);
    i->getMilk();
    Pilk *p = new Pilk("coco cola", 420, 2);
    p->drink(1337);
}
```

### Header files

Unlike python or Java C/C++ splits its files

ILoveBen.h
```cpp
int ILoveBen();
```

ILoveBen.cpp
```cpp
#include "ILoveBen.h"
int ILoveBen(){
    return 10;
}
```

main.cpp
```cpp
#include "ILoveBen.h"

int main(){
    printf("%d\n",ILoveBen());
}
```

Classes in header files example:

Ilk.h:

```cpp
#include <iostream>
#include <string>

using namespace std;

class Ilk
{
private:
    int milk;
    int private_func();

public:
    Ilk(int milk);
    ~Ilk();
    void drink(int galOfPilk);
    int getMilk();
};
```

Ilk.cpp:

```cpp
#include <iostream>
#include <string>
#include "Ilk.h"

using namespace std;

int Ilk::private_func() {
    return 69;
}

Ilk::Ilk(int milk) {
    this->milk = milk;
}
Ilk::~Ilk() {}

void Ilk::drink(int galOfPilk) {
    printf("drinking %dL of PILK\n", galOfPilk);
    printf("%d\n", this->private_func());
}
int Ilk::getMilk() {
    return this->milk;
}
```

main.cpp:

```cpp
#include <iostream>
#include <string>
#include "Ilk.h"

using namespace std;

int main() {
    Ilk *i = new Ilk(420);
    printf("%d\n",i->getMilk());
}

```


### Templates
