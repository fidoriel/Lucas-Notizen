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
#### Default ohne Args
```
class Y
{
	Y()
	{};
}
```

#### Copy Constructor
```
class Y
{
	Y& Y::Y(const Y& a);
}
```

#### Move Constructor
```
class Y
{
	Y& Y::Y(Y&& a);
}
```

#### Copy and Assignment Constructor
```
class Y
{
	Y& Y::Y(Y&& a);
}
```


## Destructor
```
class Y
{
	~Y()
	{};
}
```
called durch Stackabbau oder `delete`


## Nested Class
```
class Y
{
	class nested
	{
	}
}
```

