# errors

An idiot's attempt to do a `go` like error handling in `c++`

Really simple library and obviously the code is self documenting, take a look at the examples if you want to use.

Unfortunately there is no install rule but can be used as git submodule in a `cmake` project.

### What inspired me?

Along with `c++`, I also use `go` at least for my personal projects. And I really like how `go` handles errors without the use of any exceptions or such. How does it do that? Simple by using multiple returns, one of which is the error and then we check if the error is nil or not. Like this,

```go
f, err := os.Open("filename.ext")
if err != nil {
    //oops error
}
```

I try to imitate the same thing in `c++`, for example I can write the above example using my library as

```c++
#include <errors>
..
..
std::tie(f, err) = some_function(param);
if(err != errors::nil()){
    //oops error
}
```

The library is a header only library.

But it is still incomplete since I am yet to figure out how to imitate golang's `panic()` and `recover()`