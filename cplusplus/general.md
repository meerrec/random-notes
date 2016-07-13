#### std::string::size_type

Instead of `int`, we use `std::string::size_type` to ensure that the type is enough to represent the size of the string, no matter how big the string size is. It is an `unsigned` type object.

#### Always use `double` than `float`
On modern computers, `double` is usually much more accurate than float, and not much slower. Sometimes `double` is even faster.

#### Chain `cin` and `count`

```
cin << a << b << c;
count << a << b << c;
```

#### Vector
A `Vector` holds a sequence of values of a given type, grows as needed to accommodate additional values, and lets us get at each individual value efficiently.
```
vector<T> v;// init
vector<T>::size_type; // a type guaranteed to be able to hold the numbers of elements in the largest possible vector
v.push_back(); // stack push
v.size();
v.begin(); // first element
v.end(); // second element
```

#### sort
Defined in `<algorithm>` header, rearranges the values in a container. The arguments to `sort` specify the range of elements to be sorted. The `sort` function does its work in place, rather than creating a new container to hold the results.

#### max
Defined in `<algorithm>` header, returns the larger of two same type values.


#### typedef
Defines a synonym for type.

```
vector<double> data;
typedef vector<double>::size_type vec_sz;
vec_sz size = data.size();
```





