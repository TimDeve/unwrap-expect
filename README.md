# Unwrap/Expect

An attempt at implementing Rust's unwrap and expect in [Carp](https://www.github.com/carp-lang/carp)

## Example

```clojure
(load "git@github.com:TimDeve/unwrap-expect@v0.2.0")

(defn remote-call []
 (the (Result String String) (Result.Success @"Some data")))

(defn-do main []
  (println* (runwrap (remote-call)))
  (println* (rexpect "Remote call failed" (remote-call)))

  (println* (munwrap (Maybe.Just @"Something")))
  (println* (mexpect "Couldn't find an odd number"
                     (Array.find &(fn [x] (Int.odd? @x)) &[2 4]))))
```

## Unsafe example

`unwrap` & `expect` can be used for both Result and Maybe but the return type will match everything

```clojure
(load "git@github.com:TimDeve/unwrap-expect@v0.2.0" "unsafe-unwrap-expect.carp")

(defn main []
 (println* (Int.+ (unwrap (the (Result Int Int) (Result.Success 42)))
                  (expect "Couldn't find an odd number"
                          (Array.find &(fn [x] (Int.odd? @x)) &[2 4])))))
```
