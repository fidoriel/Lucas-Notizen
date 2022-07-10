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

wie [[#private]] aber 