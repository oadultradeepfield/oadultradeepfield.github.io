class: middle

# CS2030S PE1 Cheat Sheet

## Personal Mistakes

The condition of for loop is **recomputed** in every iteration.

```java
for (int i = 0; i < getSize(); i++) { }
```

may not work well if the return value from `getSize` changes. Additionally, if the array is **not initialized**, we cannot use for each.

---

class: middle

## Generic Templates (1/3)

### Unbounded Generics

Use when `T` can be any type.

```java
@SuppressWarnings("unchecked")
T[] items = (T[]) new Object[size];
this.items = items;
```

---

class: middle

## Generic Templates (2/3)

### Bounded Generics (`T extends Comparable<T>`)

Use when `T` must be comparable (e.g., for sorting).

```java
@SuppressWarnings({"rawtypes", "unchecked"})
T[] items = (T[]) new Comparable[size];
this.items = items;
```

---

class: middle

## Generic Templates (3/3)

### Array of Generic Types

Creating an array of generic types requires type casting.

```java
@SuppressWarnings("unchecked")
Seq<Integer>[] temp = (Seq<Integer>[]) new Seq<?>[size];
for (int i = 0; i < size; i++) {
    temp[i] = new Seq<Integer>(size);
}
```

---

class: middle

# CS2030S Midterm Cheat Sheet

## Personal Mistakes (1/2)

### Compile-time Type

- The compile-time type of any objects never change. Type casting just tell the compiler that it will be treated differently for a specific context.
- Notice that we can do `A a = (A) b` but we cannot do `b = (A) b` (`b` has a compile-time type of `B` not `A`).

---

class: middle

## Personal Mistakes (2/2)

### Type Casting with Interfaces

The code below compiles even if class `D` does not implement interface `C`:

```java
C c = (C) new D();
```

This is because Java allows the cast at compile-time, assuming `D` might later have a subclass (`E`) that implements `C`. As a result, it checks the cast at **runtime** instead.

---

class: middle

## Good to Know (1/2)

### Try-Catch Control Flow

Once an exception is **caught by a catch block**, the try-catch exits immediately **without checking subsequent catch blocks**.

### Overriding

Method overriding in $B$ (where $A <: B$) works only if $B$'s method return type and exceptions are subtypes of $A$'s.

---

class: middle

## Good to Know (2/2)

### Subtype Ordering

`byte` $<:$ `short = char` $<:$ `int` $<:$ `long` $<:$ `float` $<:$ `double`.

### Dynamic Binding Steps (Simplified)

1. **Compile Time**: Find the most specific method.
2. **Run Time**: Invoke based on the target's runtime type.
3. **Type Erasure**: If `B extends A<double>` but doesn't override the method, a **bridge method** (cast to `double`) is added.
