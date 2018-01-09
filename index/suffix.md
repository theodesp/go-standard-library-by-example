# Package Suffixarray

```
import "index/suffixarray"
```

> Package suffixarray implements substring search in logarithmic time using an in-memory suffix array.

For the purposes of the examples the following [Bacon Ipsum](https://baconipsum.com/) text is used:

> Spicy jalapeno bacon ipsum dolor amet tenderloin tail biltong, porchetta shankle hamburger shoulder ham kevin drumstick frankfurter flank. Short loin ham hock pork chop strip steak, tail doner burgdoggen flank tenderloin shankle meatball turducken t-bone buffalo. Pork chop fatback short ribs meatball boudin jowl tenderloin spare ribs sirloin pork loin frankfurter ribeye ham porchetta shoulder. Meatball sirloin burgdoggen turkey. Turducken jerky capicola frankfurter jowl rump tri-tip short loin fatback corned beef shank tongue bresaola pork loin porchetta. Pork belly flank ball tip t-bone pork chop. Porchetta cupim ham hock meatloaf frankfurter pork belly chuck.
>
> Cow strip steak chuck hamburger. Pork loin chicken porchetta, pork corned beef sausage strip steak kevin capicola ground round hamburger. T-bone turkey corned beef tail chicken bacon ball tip ham hock. Boudin pancetta corned beef pork loin. Drumstick capicola t-bone alcatra porchetta hamburger boudin chicken pork belly beef ribs ribeye beef short ribs spare ribs pork loin. Sirloin tongue pancetta leberkas salami. Pork chop capicola cow andouille jerky t-bone ham hock.

### What is a suffix Array?



### Package Index

> Contains several methods to create, lookup, save or read from an Index type.

#### type [Index](https://golang.org/src/index/suffixarray/suffixarray.go?s=711:804#L18)

Index implements a suffix array for fast substring search.

```
type Index struct {      
   // contains filtered or unexported fields
}
```

[type Index](https://golang.org/pkg/index/suffixarray/#Index)

[func New\(data \[\]byte\) \*Index](https://golang.org/pkg/index/suffixarray/#New)

[func \(x \*Index\) Bytes\(\) \[\]byte](https://golang.org/pkg/index/suffixarray/#Index.Bytes)

[func \(x \*Index\) FindAllIndex\(r \*regexp.Regexp, n int\) \(result \[\]\[\]int\)](https://golang.org/pkg/index/suffixarray/#Index.FindAllIndex)

[func \(x \*Index\) Lookup\(s \[\]byte, n int\) \(result \[\]int\)](https://golang.org/pkg/index/suffixarray/#Index.Lookup)

[func \(x \*Index\) Read\(r io.Reader\) error](https://golang.org/pkg/index/suffixarray/#Index.Read)

[func \(x \*Index\) Write\(w io.Writer\) error](https://golang.org/pkg/index/suffixarray/#Index.Write)



### Complexity

According to the implementation details time complexity is:

* `O(N*Log(N))` for index creation where N= len\(data\).
* `O(log(N)*len(s) + len(result))` for Lookup where s is the query string.
* `O(N)` for `Read` or `Write`

Space Complexity is:

* 6 bytes + 2 \* len\(N\) bytes for the `Index`
* `Read` and `Write` each allocate an intial buffer of 16384 bytes which can grow if the `N` grows.



