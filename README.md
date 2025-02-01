# Objective-C KVO and Weak References: A Common Pitfall

This repository demonstrates a common bug in Objective-C related to Key-Value Observing (KVO) and weak references.  When an object is deallocated while still being observed, attempting to send KVO notifications can lead to crashes or unexpected behavior. This example showcases the problem and provides a solution.

## The Problem

The `bug.m` file contains code illustrating the potential memory management issue.  A weak reference to an observer can cause problems if the observed object is deallocated before the observer is removed.  This happens because KVO's internal mechanism might still try to access the deallocated memory, resulting in a crash.

## The Solution

The `bugSolution.m` file provides a solution by ensuring that the observer is always removed before the observed object is deallocated. This is done by carefully managing the observer registration and removal within the object's lifecycle, particularly in `-dealloc` method or methods that can affect object's life cycle.