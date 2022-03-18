---
title: "💙 Golang1.18 Generic In Y Minutes"
date: 2022-03-18T15:21:50+09:00
draft: false
tags : [
"go",
"golang",
]
---
  With the release of golang 1.18, golang adds support to the generic.


  I strongly recommend you to watch the viedo if you want to know about generic of golang genernally
  {{< youtube id="Pa_e9EeCdy8" title="GopherCon 2021: Robert Griesemer & Ian Lance Taylor - Generics!" >}}

  I will memo some key points in this post

  There are just three things:
  - Type parameters for functions and types
  - Type sets defined by itnerfaces
  - Type inference


  ## Declare generic function
  ```golang
  type Itertor[T any] interface{
    Next() T
  }
  type sliceIter[T any] struct{
  // omit...
  }

  func NewSliceIter[T any]()Itertor[T]{
    return &sliceIter[T]{}
  }

  // types sets defined by interface
  type Number interface{
   ~int32 | float32
  }

  // type parameter for function
  func Add[T Number](a,b Number)Number{
    return a + b
  }

  type Point []int32
  func (this Point) String()string{
    return fmt.Sprintf("%v",this)
  }  

  func Scale[E Number,S ~[]E](s S,scale E)S{
    ret := make(S,len(s))
    for i,v := range s{
      ret[i] = v * scale
    }

    return ret
  }

  func Usage(){
   p := Point([]int32{1,2,3})
   fmt.Println(Scale(p,10).String())
  }

  ```

