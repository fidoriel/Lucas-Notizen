## Friend
```
class Y
{
	friend class X;
}
```

Klasse X kann auf private und protected von Y zugreifen

## Public
```
class Y
{
	public:
		int x;
}
```

alle können über `obj.x` zugeifen

## Private
```
class Y
{
	int x;
}
```

keiner können über `obj.x` zugeifen => zugriff nur innerhalb der Klassen `this.x` oder [[#Friend]]

## Protected
```
class Y
{
	protected:
		int x;
}
```

wie [[#private]] aber child Klassen haben zugriff

## Klasse/Class
```
class Y
{
		int x;
}
```

## Constructor
class Counter {
2
int c_;
//attribute 1: int, used as counter
3
int max_;
//attribute 2: int, defines the limit
4
public:
5

```
class Y
{
	Y(int m) : c_{0}, max_{m} {}
}
```
