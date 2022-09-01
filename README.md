# Validable
## Description
A ultra simple single header lib for data validation that work similar to a three valued Boolean but for any type.

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

## documentation

### Definition

```c++
template<typename _type = bool> class validable;
```
### Member types

- type
#### definition
```c++
validable<_type>::type
```
#### description
type representation

#### Example
```c++
validable<unknown_type> foo;
variable::type bar = 727;
```

### Member functions

- (constructor)
#### definition
```c++
constexpr validable();
template<typename t> constexpr validable(const t& val);
template<> constexpr validable(const type& val);
```
#### description
(1) default constructor;

(2) construct a alidablen;

(3) constructor expacialization;
#### Example
```c++
validable foo();
validable bar(727);
validable fuz(true);
```
- is_valid
#### definition
```c++
constexpr bool is_valid() noexcept;
```
#### description
used to check validity
#### Example
```c++
validable<char> bar;

/* ... */

if(bar.is_valid())
{
    /* ... */
}
```
- invalidate
#### definition
```c++
void invalidate() noexcept;
```
#### description
change the state of the oject

#### Example
```c++
validable foo;

/* ... */

foo.invalidate();
```
- validate
#### definition
```c++
void validate() noexcept;
```
#### description
change the state of the oject

#### Example
```c++
validable foo;

/* ... */

foo.validate();
```


- value
#### definition
```c++
constexpr const type& value();
```
#### description
returns a const reference to the value;

#### Example
```c++
validable<double> foo(0.27);
auto bar = foo.value() + 727.0;
```


- reference
#### definition
```c++
constexpr type& reference();
```
#### description
returns a reference to the value, this should be avoided!;
#### Example
```c++
validable<double> foo(0.27);
foo.reference() += 727.0;
```

- set
#### definition
```c++
template<typename t> void set(const t& val) noexcept;
template<> void set(const type& val) noexcept;
```
#### description
assigning the value 
#### Example
```c++
validable<char> foo;
foo.set("a");
```

- reset
#### definition
```c++
void reset()
```
#### description
Reset to default, as if the object is invalidated;
#### Example
```c++
validable foo(true);
foo.reset();
```

- (type)
#### definition
```c++
operator type();
```
#### description
Cast to the object type;
#### Example
```c++
validable<std::string> foo;
auto bar = (foo::type)foo;
```




### Non-member functions

- operator<<
#### definition
```c++
template <typename _CharT, typename type> std::basic_ostream<_CharT>& operator<<(std::basic_ostream<_CharT>& _Os, const validable<type>& _Right) noexcept;
```
#### description
#### Example
```c++
validable<int> foo;
std::cout << foo;
```
- operator>>
#### definition
```c++
template <typename _CharT, typename type> std::basic_istream<_CharT>& operator>>(std::basic_istream<_CharT>& _Is, const validable<type>& _Right);
```
#### description
Cast to the object type;
#### Example
```c++
validable<int> foo;
std::cin >> foo;
```