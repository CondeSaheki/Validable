# Validable
## Description
A ultra simple single header lib for data validation that work similar to like a three valued Boolean logic but can contain any type.



## Example

```c++
#include "validable.h"

/*...*/

nimiat::validable<uint64_t> foo;
nimiat::validable<bool> bar;

foo.set(727);

std::cout << "foo is " << foo; // is valid
std::cout << "bar is " << bar; // is invalid

foo.invalidate();

std::cout << "foo is " << foo; // is invalid
```

## Reference

### Definition

```c++
template<typename _type = bool> class validable;
```
### Member types

```c++
type
```


### Member functions


```c++
(constructor)
```
```c++
is_valid
```
```c++
invalidate
```
```c++
validate
```
```c++
value
```
```c++
reference
```
```c++
set
```
```c++
reset
```
```c++
(type)
```


Non-member functions

```c++
operator<<
```
