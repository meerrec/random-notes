#### std::string::size_type

Instead of `int`, we use `std::string::size_type` to ensure that the type is enough to represent the size of the string, no matter how big the string size is. It is an `unsigned` type object.
