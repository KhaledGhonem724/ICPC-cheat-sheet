# PUA ECPC 2023 cheat sheet 
## Content
- [libraries](#libraries)
- [code templates](#code-templates)
- [input and output](#input-and-output)
- [important built-in functions](#important-built-in-functions) 
- [Arrays](#Arrays) 
- [STLs](#STLs) 
- [important functions](#important-functions) 
- [background](#background)
- [bit manipulation](#bit-manipulation)
- [matrices](#matrix)
- [maths](#maths)
- [goniometry](#goniometry) 

## libraries
```cpp
#include <limits>
#include <iomanip>
#include <cstdlib>
#include <cstdio>
#include <iostream>
#include <cassert>

#include <string>
#include <string.h>

#include <vector>
#include <list>
#include <queue>
#include <stack>
#include <deque>
#include <map>
#include <unordered_map>
#include <set>
#include <unordered_set>

#include <bitset>

#include <algorithm>
#include <numeric>
#include <cmath>
```
## code templates
### standard
```cpp
using namespace std;
```

### data types define
```cpp
#define ll long long
```
## input and output
### Input from Files 
Input may be from file, use the same file name stated in the statement.<br>
C++  	
```cpp 
freopen("inputfile.in", "r", stdin);
```
```cpp 
#include<fstream>
ifstream fin("student.doc");
int rno,fee;
fin>>rno>>fee;   //read data from the file student
fin.close();
```
Java 
```java
InputStream inputStream = new FileInputStream("inputfile.in");
```
```java
import java.io.File;
import java.util.Scanner;
File file = new File("test.txt");
Scanner sc = new Scanner(file);
String s= sc.next();
```
### fast input and output
```cpp
ios_base::sync_with_stdio(0);
cin.tie(0);
cout.tie(0);
```
### printf function
printf( ${\color{blue}string}$ , ${\color{red}value}$); <br/>
the ${\color{blue}string}$ represents the exact format which will be printed. <br/>
it must include the sign `%` because the parameter ${\color{red}value}$ will be placed in it's place. <br/>
the sign `%` in the ${\color{blue}string}$ is followed by a character representing the data type of the ${\color{red}value}$  as in the examples.<br/>
assume :
```cpp
double n = 97.1234;
```
**example 1 :**
```cpp
printf("print 1: the value %c is perfect \n", n);	//print char
printf("print 2: the value %d is perfect \n", (int)n);	// print integer
printf("print 3: the value %f is perfect \n", n);	// print double 
printf("print 4: the value %e is perfect \n", n);	// print double as exponent notation (scientific) 
printf("print 5: the value %o is perfect \n", (int)n);	// print int as octal
printf("print 6: the value %x is perfect \n", (int)n);	// print int as hexa
printf("print 7: the value %a is perfect \n", n);	// print double as hexa
```
**output 1 :**
```
print 1: the value Σ is perfect
print 2: the value 97 is perfect
print 3: the value 97.123400 is perfect
print 4: the value 9.712340e+01 is perfect
print 5: the value 141 is perfect
print 6: the value 61 is perfect
print 7: the value 0x1.847e5c91d14e4p+6 is perfect
```
the sign `%` in the ${\color{blue}string}$ may also be followed by `number` or `.number` representing the `minimum langth` of the  ${\color{blue}string}$. <br/>
if the string was shorter than the `minimum langth` :
in case of `number` the sequence of `spaces` was added to the begining of the string. <br/>
in case of `.number` the sequence of `zeros` was added to the begining of the string. <br/>
**example 2 :**
```cpp
printf("%d", (int)n);
printf("\n");
printf("%6d", (int)n);
printf("\n");
printf("%.6d", (int)n);
```
**output 2 :**
```
97
    97
000097
```
an exeption of this rule is when the value data type is `double` ,in this case ,the `.number` represent the number of digits after the decimal point. <br/>
**example 3 :**
```cpp
printf("%f", n);
printf("\n");
printf("%12f", n);
printf("\n");
printf("%.12f", n);
```
**output 3 :**
```
97.123400
   97.123400
97.123400000000
```


## important built in functions 
### String
```cpp
to_string(int);
stoi(string);
isalpha(ch);
isdigit(ch);
```
### numbers
```cpp
min(a,b);
max(a,b);
swap(a,b);
floor(a);
ceil(a);
round(a);
sqrt(a); //used to calculate the square root of number
cbrt(a); //used to calculate the cube root of number
abs(a);  //returns the absolute value of number
pow(a,b);
log2(a);
```
## Arrays
Note :
`arr , arr+size` === `v.begin(), v.end()` <br>
`arr , arr+size` used with an array<br>
`v.begin(), v.end()` used with any STLs
- **basic**
```cpp
sort( v.begin(), v.end());
reverse( v.begin(), v.end() );
fill( v.begin(), v.end() , val );
find(v.begin(), v.end(), a);

int MinValue = *min_element( v.begin(), v.end());
int MaxValue = *max_element( v.begin(), v.end() );
int index = find( v.begin(), v.end() , val ) -v.begin();
int index = find( arr, arr+size , val ) -arr;

```
- **advanced**
```cpp
next_permutation( arr , arr + size );
upper_bound( arr , arr + size , val );// time : log2(size) + O(1) 
// Returns the address of the first element e when ( e > val ) arr is sorted
index = upper_bound(arr,arr+7, 3) - arr;
value = *upper_bound(arr,arr+7, 3);
```
## STLs
- **map**
```cpp
map_name.insert({ key, val });
map_name.insert(iterator position, {key, element});// inserts element in position (for unordered map)
mp2.insert(mp1.begin(), mp1.end());// inserts all elements in range [begin, end] from mp1 into mp2
auto it = map_name.find(key);// O(log n)
map_name.erase(it);// O(1)
map_name.erase(key);// O(1)
map_name.upper_bound(key);// upper_bound of the parameter key is returned
map1_name = map2_name;//the map2 is assigned into map1 by destroying map1's elements // O(n*log n)
map_name.count(key)
```
- **set**
```cpp
set_name.insert(element);
set_name.insert(iterator position,  element);// inserts element in position (for unordered set)
set2.insert(set1.begin(), set1.end());// inserts all elements in range [begin, end] from set1 into set2
auto it = map_name.find(key);// O(log n)

//set_name : 1, 2, 3, 4, 5
position= 2
myset.erase(position);
//set_name : 1, 2, 4, 5

//set_name : 1, 2, 3, 4, 5, 6, 7, 8 
pos1= 3, pos2= 6
myset.erase(pos1, pos2);
//set_name : 1, 2, 3, 8

set_name.emplace(value);
//The value is added to the set if the set does not contain that element already.

set_name.upper_bound(value);// upper_bound of the value is returned
set2_name.swap(set2_name); // O(1)
set_name.count(element); //The function returns 1 or 0 as the set contains unique elements . //O(log n)
```
- **map and set time complexity** <br>
<br>
<img src="STLs1.png" width="550" title="hover text"><br>


## important functions 
### GCD
Greatest Common Divisor (GCD) or Highest Common Factor (HCF) of two numbers is the largest number that divides both of them. 
```cpp
int GCD(int a, int b) {
	if (!b)return a;
	return GCD(b, a % b);
}
```
### LCM
Least Common Multiple (LCM) of two numbers is the smallest number which can be divided by both numbers. 
```cpp
int LCM(int a, int b)
{
    return (a / GCD(a, b)) * b;
}
```


## background 
### ASCII
| char  | ASCII |
| ------ | -------- |
| 0 – 9  | 48 – 57  |
| A – Z  | 65 – 90  |
| a – z  | 97 – 122 |

## bit manipulation
### count bits
```cpp
int countNumBits(int mask) {
	int ret = 0;
	while (mask) 	{
		mask &= (mask-1);
		++ret;	// Simply remove the last bit and so on
	}
	return ret;
}
```
### print submasks of a length
```cpp
void printAllSubsets(int len){
	for (int i = 0; i < (1<<len); ++i)
		printNumber(i, len);
}
```
### print submasks of a mask
Note : this code doesn't print 0
```cpp
void getAllSubMasks(int mask) {

	for(int subMask = mask ; subMask ; subMask = (subMask - 1) & mask)
		printNumber(subMask, 32);	
}
```
### graycode 
```cpp
int getGrayCode(int n){
	return n^(n>>1);
}
```
## matrix
  <img src="matrix.png" width="550" title="hover text"><br>

## maths
to check if n is :<br>
divisible by 8 : last 3 digits of n is forming a number which is divisible by 8

## goniometry
the length between (x1,y1) and (x2,y2) is :
```cpp
double len = sqrt( pow(x2-x1 , 2) + pow(y2-y1 , 2) ); 
```
