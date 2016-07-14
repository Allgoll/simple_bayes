# Simple Bayes

A Simple Bayes (a.k.a. [Naive Bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier)) implementation in Elixir.

## Features

- [x] Naive Bayes algorithm
- [x] no external dependencies
- [x] optional keywords weighting
- [x] ignore English stop words
- [ ] [additive smoothing](https://en.wikipedia.org/wiki/Additive_smoothing)

## API

```elixir
bayes = SimpleBayes.init
        |> SimpleBayes.train(:apple, "red sweet")
        |> SimpleBayes.train(:apple, "green", weight: 0.5)
        |> SimpleBayes.train(:apple, "round", weight: 2)
        |> SimpleBayes.train(:banana, "sweet")
        |> SimpleBayes.train(:banana, "green", weight: 0.5)
        |> SimpleBayes.train(:banana, "yellow long", weight: 2)
        |> SimpleBayes.train(:orange, "red")
        |> SimpleBayes.train(:orange, "yellow sweet", weight: 0.5)
        |> SimpleBayes.train(:orange, "round", weight: 2)

bayes |> SimpleBayes.classify_one("Maybe green maybe red but definitely round and sweet.")
# => :apple

bayes |> SimpleBayes.classify("Maybe green maybe red but definitely round and sweet.")
# => %{
#   apple:  -10.492915521902894,
#   orange: -12.544068044350276,
#   banana: -14.706795341847975
# }
```

## License

Licensed under [MIT](http://fredwu.mit-license.org/)