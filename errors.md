# Errors

```
import "errors"
```

> Package errors implements functions to manipulate errors…

### Package Index

There is only one function so far…

#### func [New](https://golang.org/src/errors/errors.go?s=293:320#L1)

```go
func New(text string) error
```

_New returns an error that formats as the given text._

---

#### **Example Usage and Notes**

* **Return as error**

_Just call \*New\* with a short description of the error_

```go
f, err := os.Open(path)
if err != nil {
   return nil, errors.New("open failed")
} 
defer f.Close()
```

---

* **Save as variable and reuse**

Save the result struct in a variable and reuse it when needed

```go
var OpenFailed = errors.New("open failed")
func ReadFile(path string) ([]byte, error) {
    f, err := os.Open(path)
    if err != nil {
       return nil, OpenFailed
    }
    defer f.Close()
    ...
}
```

---

* **A note about error strings from **[**Go Code Review Guide**](https://github.com/golang/go/wiki/CodeReviewComments#error-strings)

> Error strings should not be capitalized \(unless beginning with proper nouns or acronyms\) or end with punctuation, since they are usually printed following other context.
>
> That is, use `fmt.Errorf("something bad")` not `fmt.Errorf("Something bad")`, so that `log.Printf("Reading %s: %v", filename, err)` formats without a spurious capital letter mid-message.
>
> This does not apply to logging, which is implicitly line-oriented and not combined inside other messages.

---

* **Different allocations should not be equal**

…as they create 2 different error objects

```go
errors.New("open failed") != errors.New("open failed")
```

---

#### **Complete example**![](https://cdn-images-1.medium.com/max/1000/1*fn5OgYYFUBw8s8p77aY84g.png)[![](/assets/run-code.png)](https://play.golang.org/p/qhNorvt5CvE)

> Internally New assigns the string to a struct that implements the Error\(\) interface.

## Questions

* **Why Error strings Should Not be capitalised in Go?**

  _**Answer**: Because they are usually printed following other context._

* **Are 2 errors with the same message string the same?**

  _**Answer**: No, because they have different allocations._

[^1]: [Alternative link](https://play.golang.org/p/qhNorvt5CvE)

