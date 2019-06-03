# boost-ts
TypeScript Library to boost functional programming

### Tuple Type Library

#### Push

Add a type to the head of type tuple.

```TypeScript
// Target = [boolean, string, number]
type Target = Push<boolean, [string, number]>
```

#### Pop

Remove a type from the head of type tuple.

```TypeScript
// Target = [string, number]
type Target = Pop<[boolean, string, number]>
```

#### Head

Get the head of type tuple.

```TypeScript
// Target = boolean
type Target = Head<[boolean, string, number]>
```

#### Reverse

Reverse the order of type tuple.

```TypeScript
// Target = [number, string, boolean]
type Target = Reverse<[boolean, string, number]>
```

#### Filter

Filter a type from type tuple.

```TypeScript
// Target = [boolean, number]
type Target = Filter<string, [boolean, string, number]>
```

#### Select

Select a type from type tuple.

```TypeScript
// Target = [string, number]
type Target = Select<string|number, [boolean, string, number]>
```

#### Zip

Zip two type tuples.

```TypeScript
// Target = [ [1, boolean], [2, string, [3, number] ]
type Target = Zip<[1, 2, 3], [boolean, string, number]>
```

### Number Type Library

### Decrease

Decrease a number type.

```TypeScript
// Target = 3
type Target = Decrease<4>
```


### Comp

Compare two number types.

```TypeScript
// Target1 = -1
type Target1 = Comp<1, 2>
// Target2 = 0
type Target2 = Comp<2, 2>
// Target3 = 1
type Target3 = Comp<2, 1>
```

### Partial Function Call

This library offers a partial function call with flexible argument binding. Of course, it's __type safe__.

```TypeScript
import { partial, _1, _2 } from "boost-ts/lib/partial"

function sub (a:number, b:number):number {
    return a - b
}

// bind 2nd argument
const sub10 = partial(sub, _1, 10)        // type :: (a:number)=>number
console.log(sub10(100))                   // output is 90

// swap 1st and 2nd argument
const reverse_sub = partial(sub, _2, _1)  // type :: (a:number, b:number)=>number
console.log(reverse_sub(10, 100))         // output is 90
```


------
- Some code of this library is based on [this stackoverflow article](https://stackoverflow.com/questions/54607400/typescript-remove-entries-from-tuple-type).
- The API of partial function is inspired by [Boost C++ library](https://www.boost.org/)
