## Some Notes

[TOC]

### Generic functions

#### [accumlate](https://msdn.microsoft.com/zh-cn/library/aawk6wsh(v=vs.71).aspx "accumlate")

> it is included in `#include <numberic>`

its convinent to get sum, it provides a new way to connect some strings.
**for example**
```c++
#include <iostream>
#include <numberic>
#include <string>
#include <vector>

using namespace std;

int main()
{
	vector<string> v_str;
	for(int i = 0; i < 5; i++)
	{
		v_str.push_back("abc");
	}
	
	string str = accumlate(begin(v_str), end(v_str), string(""));
	cout << str << endl;
	return 0;
}
```
**Result**
> abcabcabcabcabc

#### [back_inserter](http://www.cplusplus.com/reference/iterator/back_inserter/)

#### Graphic
 top sort
 
#### Heap Sort


Tencent, Give me some hope...plz
