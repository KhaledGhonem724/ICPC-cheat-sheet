# PUA ECPC 2023 cheat sheet 
## Content
- [code templates](#code-templates)
- [input and output](#input-and-output)
- [important built-in functions](#important-built-in-functions) 
- [Arrays](#Arrays) 
- [Set & Map](#Set-&-Map) 
- [important functions](#important-functions) 
- [bit manipulation](#bit-manipulation)
- [maths](#maths)
- [goniometry](#goniometry) 

## code templates
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

#define ull unsigned long long 
#define ll long long
#define fastinout                 \
	ios_base::sync_with_stdio(0); \
	cin.tie(0);                   \
	cout.tie(0);
#define testcases \
	ll t;         \
	cin >> t;
#define all(x) (x).begin(), (x).end()
#define print(x)          \
	for (auto i : (x))    \
	{                     \
		cout << i << " "; \
	}
#define mkp make_pair
using namespace std;
```
## input and output
### Input from Files 
Input may be from file, use the same file name stated in the statement.<br>
```cpp 
#include<fstream>
ifstream fin("student.doc");
ofstream fout("student.doc");
fin>>num; fout<<num;  // read/write data from/to the file student
fin.close();fout.close();
```
### fast input and output
```cpp
ios_base::sync_with_stdio(0);
cin.tie(0);
cout.tie(0);
getline(cin, s);
```
### getline
```cpp
getline(cin, s);
```
### printf function
```cpp
%c	// print char
%d 	// print integer
%f	// print double 
%e	// print double as exponent notation (scientific) 
%o	// print int as octal
%x	// print int as hexa
%a	// print double as hexa
```
the sign `%` may also be followed by `number` or `.number`  <br/>
in case of `number` the sequence of `spaces` was added to the begining of the string. <br/>
in case of `.number` the sequence of `zeros` was added to the begining of the string. <br/>
```cpp
printf("%d", 97); 		//97
printf("%6d", 97);		//    97
printf("%.6d", 97);		//000097
```
when the value data type is `double` ,in this case ,the `.number` represent the number of digits after the decimal point. <br/>
```cpp
printf("%f", n);	//97.123400
printf("%12f", n);	//   97.123400
printf("%.12f", n);	//97.123400000000
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
min(a,b);	max(a,b);	swap(a,b);
floor(a);	ceil(a);	round(a);
abs(a);		pow(a,b);	log2(a);
sqrt(a);	cbrt(a); //cube root 
```
## Arrays
- **basic**
```cpp
sort( v.begin(), v.end());
reverse( v.begin(), v.end() );
fill( v.begin(), v.end() , val );
find(v.begin(), v.end(), a);
int index = find( v.begin(), v.end() , val ) -v.begin();
int MinValue = *min_element( v.begin(), v.end());
int MaxValue = *max_element( v.begin(), v.end() );
```
- **advanced**
```cpp
next_permutation( v.begin(), v.end());
upper_bound(  v.begin(), v.end() , val );	//first element e when ( e > val ) arr is sorted
lower_bound(  v.begin(), v.end() , val );	//first element e when ( e >= val ) arr is sorted
index = upper_bound( v.begin(), v.end(), 3) - v.begin();
value = *upper_bound( v.begin(), v.end(), 3);
```
## Set & Map
```cpp
// positions are 0 indexed
set_name.insert(element);
set_name.insert(iterator position,  element);	// for unordered set
set2.insert(set1.begin(), set1.end());	// inserts all elements in range [begin, end]
myset.erase(position);		// delete element in position 
myset.erase(pos1, pos2);	// delete all elements from pos1 to pos2 inclusive
myset.erase(key);		// in maps
// returns 1 if the key element is found in the map else returns 0. 
auto it = set_name.find(num);	// with maps num => the key
set2_name.swap(set2_name); 	// O(1)
set_name.count(element); 	// O(log n)
```
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
## maths
to check if n is :<br>
divisible by 8 : last 3 digits of n is forming a number which is divisible by 8

## goniometry
the length between (x1,y1) and (x2,y2) is :
```cpp
double len = sqrt( pow(x2-x1 , 2) + pow(y2-y1 , 2) ); 
```
