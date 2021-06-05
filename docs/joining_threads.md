# Joining threads

## Introduction

`std::thread` object represents the execution of an underlying thread which is being managed by the
OS scheduler. There are 2 main ways to construct a new thread object (_for the sake of this
explaination let's forget about move construction_)

```cpp
thread() noexcept;                             // 1

template <typename Func, typename ... Args>
explicit thread(Func&& func, Args&& ... args); // 2

```

  1. The _default constructed_ thread does not represent any underlying thread of execution.

  2. The thread constructor receives a callable object as the parameter along with the arguments that
  are passed to callable object. Once the thread object is constructed a new thread of execution
  is already started which executes `func` function with the `args` arguments.

Once a thread is started, you need to explicitly decide one of the following,
  1. wait for the thread to finish _i.e._ join with the thread
  2. leave to run on its own _i.e._ put the thread into a detached state

## What is thread joining

