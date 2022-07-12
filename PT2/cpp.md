### Const
```
const int version {401}; // nach dem Initialisieren keine Änderung möglich
static const int real_version {4013}; // int-Konstante, internal linkage
constexpr int getRealVersion() { return real_version; } // const-Ausdruck
```