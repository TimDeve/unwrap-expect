# Unwrap/Expect

An attempt at implementing Rust's unwrap and expect in [Carp](https://www.github.com/carp-lang/carp)

## Example

```clojure
(defn main []
 (println* (+ (unwrap (Maybe.Just 42)
              (expect "Couldn't find an odd number"
                      (Array.find &(fn [x] (Int.odd? @x)) &[2 4])))))
```
