### Constexpr, Const und static
```
const int x = 42; // nicht mutierbar
constexpr int get42() { return 42; } // evaluated at compile time
static int x = 42; // Variable wird beim ersten Anfassen intialisiert und bleibt Initialisiert
static const x = 42; // Wie static nur nicht mutierbar
```

### Trinärer Operator
```
condition ? statement true : statement false
```

### Switch
```
switch (i) {
	case 1: ;
	case 2: ;
	case 3: ;
	case 4: ;
	case 5: ;
		break;
	case 6: ;
	}
```

### GOTO
_Why goto statement considered harmful_
=> Nested loops??
```
int main () {
	LOOP:do {
	  if(1) {
		 goto LOOP;
	  }
	}
}
```

### Threading
```
#include <thread>
int n = 42;
std::thread t2(function_1, 42); // pass by value
std::thread t3(function_2, std::ref(n)); // pass by reference
t2.join();
t3.join();
```

### Function Specials
```
void point(int x = 3, int y = 4); // defaults
```

```
void f (const int n) {;} // n constand in body
```

```
int d(int & x); // by reference
```

```
void f (int n) {;} // overloading
void f (int n, int m) {;} // overloading
```

### Generic/Tamplating
```
template<typename T>
void printLine(T s) { std::cout << s; }

// calling
printLine<double>(1);
printLine<>('a'); // printLine<char>('a');
printLine(7); // calls printLine<int>(7);
```

### Namensräume
- Global `::X`
- namespace: `namespace x{ namespace y {...}}`
	- Unbenannt: `namespace {...}`
	- `using namespace std;`

### Errors, Failiures, Faults
```
try
{
	if(1)
		throw 1;
}
catch (int x)
{
}
```
Custom Exception
```
class myexception: public exception
{
  virtual const char* what() const throw()
  {
    return "My exception happened";
  }
} myex;

int main () {
  try
  {
    throw myex;
  }
  catch (exception& e)
  {
    cout << e.what() << '\n';
  }
  return 0;
}
```

### algorithm
#### Suchen
```
std::vector<int> myvector;
std::vector<int>::iterator it = std::find_if(myvector.begin(), myvector.end(), [](int i){ return i % 2; });
```
immer `it != myvector.end()` prüfen
#### Duplicate elimination
```
std::vector<int>::iterator it = std::unique(myvector.begin(), myvector.end());
```

#### weitere:
```
std::sort(x.begin(), x.end());
merge(v1.begin(),v1.end(),v2.begin(),v2.end(),target.begin());
```
