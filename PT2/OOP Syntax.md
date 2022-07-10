## Friend
```
class Y
{
	friend class X;
}
```

Klasse X kann auf private und protected von Y zugreifen
wird nicht vererbt

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
wird nicht vererbt
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
	Y& Y::operator=(const Y&);
}
```
gibt den Pointer weiter `objA = objB;`

## Destructor
```
class Y
{
	~Y()
	{};
}
```
called durch Stackabbau oder `delete`
Erst ~Kind, dann ~Eltern aufgerufen
in Vererbungshirachien Eltern `virtual`
## Nested Class
```
class Y
{
	class nested
	{
	}
}
```

## Methoden
```
class Y
{
	int x; // private
	public:
		void doX()
		{
			this.x = 42;
		};

		void getX() const
		{
			return this.x;
		};
}
```

nicht modifizierende Methoden mit `const`

## Vererbung
### Public
```
class X { ... }; // keine vererbung
class Y : public X { ... }; // erbt von class X
class Z : public Y { ... }; // erbt von class Y und Transitiv von X
```
Class members von X ändern ihren Zugriffsschutz nicht

### Private
```
class X { ... }; // keine vererbung
class Y : private X { ... };
```
Y erbt alle Attribute(private, protected, public) von X als private

### Protected
```
class X { ... }; // keine vererbung
class Y : proteted X { ... };
```
Y erbt private und protected von X als protected

## Virtual
```
class P {
	public:
		virtual void f() {};
};

class C : public P {
	public:
		virtual void f() {}; // überschreiben von f

		virtual void g() { P::f(); } // verwenden von Parent f
};
```
überschreibt eine 

## Abstrakte Basisklasse
nur Funktionsskelett, keine Impl, muss zwingend geerbt bzw. überschrieben werden
```
class P {
	public:
		virtual void x() const;
		virtual void y();
};
```

## Override
```
class U {
	public:
		virtual void f() {}
};
class V : public U {
	public:
		void f(int x) override {} // Compiler Error
};
```

Prüft auf Signaturgleiche f(int x) $\neq$ f()

## Final
```
class U {
	public:
		virtual void f() {}
};

class V : public U {
	public:
		virtual void f() final {}
};

class W : public V {
	public:
		void f() {} // Compiler Error
};
```
Final ist nich überschreibbar, selbes bei klassen
```
class X final {
	public:
		void f() {}
};

class Y : public X { // Compiler Error
	public:
		void g() {}
};
```

## Casting
### Upcasting
->Child => ->Parent
```
class U {};
class V : public U {};

V* p1 = new V;
U* p2 = new U;
U* p3 = p1; // up casting, implicit
U* p4 = static_cast<U*>(p1); // up casting using static_cast
U& r1 = *p2; // ok
U& r2 = *p1; // ok, up casting
```

### Downcasting
->Parent => ->Child
nur wenn Child Spezialisiert
laufzeitgeprüft durch `dynamic_cast`
```
class U { public: virtual ~U(){} };
class V : public U {};

V* p1 = new V;
U* p2 = new U;

U* p3 = static_cast<U*>(p1); // ok, up casting
V* p4 = static_cast<V*>(p3); // in this case ok
V* p5 = dynamic_cast<V*>(p3); // in this case ok
std::cout << "p5: " << p5 << std::endl;

class X { public: virtual ~X(){} };
X* p6 = new X;
V* p7 = dynamic_cast<V*>(p6); // does not make sense
std::cout << "p7: " << p7 << std::endl; // p7 is nullptr
```
