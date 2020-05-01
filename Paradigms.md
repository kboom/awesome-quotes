# Object-Oriented

The guiding principle of object-oriented programming is “autognosis”, meaning “only having knowledge of one’s self”.


# Functional

## Functor
A bag with map operation

## Monad

A monad is an "amplifier" of types that obeys certain rules and which has certain operations provided. This allows monads to simplify a wide range of problems, like handling potential undefined values (with the Maybe monad), or keeping values within a flexible, well-formed list (using the List monad). With a monad, a programmer can turn a complicated sequence of functions into a succinct pipeline that abstracts away additional data management, control flow, or side-effects.

A bag with unit and flatMap (or map and flatten) functions (a functor which knows how to flatten)


## Lenses

```js
var bigBird = {
  name: "Big Bird",
  age:6,
  comments:[
    {body:'sing, sing a song',title:'Line 1'},
    {body:'make it simple',title:'Line 2'},
    {body:'sing out strong',title:'Line 3'}]
};

lensOver('comments', map( lensOver('body', capitalizeFirst) ))(bigBird);
/*
{
 "name": "Big Bird",
 "age": 6,
 "comments": [
  {"body": "Sing, sing a song", "title": "Line 1"},
  {"body": "Make it simple", "title": "Line 2"},
  {"body": "Sing out strong", "title": "Line 3"}
 ]
}
```



[Monads in 15 minutes](https://nikgrozev.com/2013/12/10/monads-in-15-minutes/)


