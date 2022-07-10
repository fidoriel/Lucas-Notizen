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

### Mehrfach Vererbung
```
class X {
	virtual void g() {}
	virtual void h() {}
	virtual void i() {}
};
class Y {
	virtual void g() {}
	virtual void h() {}
};
class Z : public X, public Y {
	virtual void g() {}
};

// OK
std::unique_ptr<D> p {new Z()};
p->g(); // wegen g() aus D
p->h(); // Namenskonfilikt
p->X::h(); // Name Spetifiziert
p->i // i() aus X
```

#### Mehrfache Namensnennung
```
class B {
	virtual void g() {}
};

class D1 : virtual public B {
};

class D2 : virtual public B {
};

class E : public D1, public D2 {
	public:
		virtual void g() override {} // D::g()
};
```
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

## Shadowing
Überschreiben einer Methode/Variable, ohne dass die Elternklasse [[#Virtual]] oder [[#Override]]
!maybe

## Casts
### const_cast
Entfernt Konstantheit
```
int i = 3; // i is not declared const
const int& cref_i = i; // const reference to i
const_cast<int&>(cref_i) = 4; // OK: modifies i via cref_i
```

### static_cast
für up/down Casting
Typüberwacht
```
float x = 4.26;
int y = x; // C like cast
int z = static_cast<int>(x);
```

### dynamic_cast
```
struct Base {
	virtual ~Base() {}
};
struct Derived : Base {
	virtual void name() {}
};

// BSP:
Base* b2 = new Derived;
if(Derived* d = dynamic_cast<Derived*>(b2)) {
	std::cout << "downcast from b2 to d successful\n";
	d->name(); //safe to call not NULL
}
```

### reinterpret_cast
stumpfer cast ohne checks => c cast
für Memory mapped IO etc.
```
int* p = new int(65);
char* ch = reinterpret_cast<char*>(p);
```