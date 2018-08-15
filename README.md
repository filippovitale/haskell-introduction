# Haskell Introduction hands-on tutorial

## GHC Haskell REPL

```bash
# spinup this image ---\
#                      |
#                      ,

docker run -it --rm haskell ghci

#                            ^
#                            |
# running the Haskell REPL --|

# `-it`  <-- interactive mode
# `--rm` <-- remove the container when terminated
```


## Getting familiar with the syntax

```haskell
-- Let's play with List -------------------------------------------
Prelude> [1,2,3]
[1,2,3]

Prelude> head [1,2,3]
1

Prelude> :t head
head :: [a] -> a
-- ----------------------------------------------------------------

-- Let's play with String/Char ------------------------------------
Prelude Data.List Data.Char> :t ""
"" :: [Char]

Prelude Data.List Data.Char> :m + Data.List Data.Char
Prelude Data.List Data.Char> text <- readFile "/root/LICENSE.md"

Prelude Data.List Data.Char> head text
'C'

Prelude Data.List Data.Char> take 9 text
"Copyright"

Prelude Data.List Data.Char> :t take
take :: Int -> [a] -> [a]
-- ----------------------------------------------------------------

-- Let's play with words ------------------------------------------
Prelude Data.List Data.Char> head (words text)
"Copyright"

Prelude Data.List Data.Char> :t words
words :: String -> [String]

Prelude Data.List Data.Char> :t ($)
($) :: (a -> b) -> a -> b

Prelude Data.List Data.Char> head $ words text
"Copyright"
-- ----------------------------------------------------------------

-- Let's play with function composition ---------------------------
Prelude Data.List Data.Char> :t (.)
(.) :: (b -> c) -> (a -> b) -> a -> c

Prelude Data.List Data.Char> :t (head . words)
(head . words) :: String -> String

Prelude Data.List Data.Char> (head . words) text
"Copyright"

Prelude Data.List Data.Char> head . words $ text
"Copyright"

Prelude Data.List Data.Char> :t map
map :: (a -> b) -> [a] -> [b]

Prelude Data.List Data.Char> :t toLower
toLower :: Char -> Char

Prelude Data.List Data.Char> head . words . (map toLower) $ text
"copyright"
-- ----------------------------------------------------------------
```


## What kind of language Haskell is

* Non-strict, Pure functional programming language
* Functions are first-class values
* Application Domain is described by types


## Let's write a functional program

* using pure I/O actions and functions
* expressing both data and processing by types
  * not the steps to execute for achieving the results
* abstracting using type classes
