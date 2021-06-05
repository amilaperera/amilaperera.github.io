# Joining threads

## Introduction

`std::thread` object represents the execution of an underlying thread which is being managed by the
OS scheduler. There are 2 main ways to construct a new thread object (_for the sake of this
explaination let's forget about move construction_)

```c++
thread() noexcept;

template <typename Func, typename ... Args>
explicit thread(Func&& func, Args&& ... args);

```

## What is thread joining

