Static methods (for a _class_) are not callable when a class is instantiated,
but they may be called directly from the class they occur within.

```js
class Triple {
  static triple(n) {
    n = n || 1; //should not be a bitwise operation
    return n * 3;
  }
}

class BiggerTriple extends Triple {
  static triple(n) {
    return super.triple(n) * super.triple(n);
  }
}

console.log(Triple.triple());        // 3
console.log(Triple.triple(6));       // 18
console.log(BiggerTriple.triple(3)); // 81
var tp = new Triple();
console.log(BiggerTriple.triple(3)); // 81 (not affected by parent's instantiation)
console.log(tp.triple());            // 'tp.triple is not a function'.
```
