# RSolve

A general solver for type checking for programming languages and real world puzzles with complex constraints. 


## About

A Hello World program could be found at `src/Main.hs` to solve a complex problem.

The descriptions for this problem are presented through following link:

https://www.zhihu.com/question/68411978/answer/332459717.


Also, much easier cases using the same background as above problem (logic constraints described with four options `A, B, C, D`) could be enjoyale:

```haskell
test2 = do
  a <- store $ sol [A, B, C]
  b <- store $ sol [B, C, D]
  c <- store $ sol [C]
  _ <- solve $ a `eq`  b
  _ <- solve $ b `neq` c
  _ <- solveNeg  -- `Not` condition requires this
  _ <- solvePred -- unnecessary
  mapM require [a, b, c] 
  
main = do
    format ["a", "b", "c"] . nub . L.map fst
    $ runBr test2 emptyLState
```

output:

```
λ stack exec RSolve
====
"a" : Sol (fromList [B])
"b" : Sol (fromList [B])
"c" : Sol (fromList [C])
```