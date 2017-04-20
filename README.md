# MoreLINQ

LINQ to Objects is missing a few desirable features.

This project enhances LINQ to Objects with extra methods, in a manner which
keeps to the spirit of LINQ.

MoreLINQ is available for download and installation as
[NuGet packages](https://www.nuget.org/packages/morelinq/).

Documentation for the stable and beta releases can be found at
[morelinq.github.io](http://morelinq.github.io/).


## Usage

MoreLINQ can be used in one of two ways. The simplest is to just import the
`MoreLinq` namespace and all extension methods become instantly available for
you to use on the types they extend (typically some instantiation of
`IEnumerable<T>`). In some very rare instances, however, this cause conflicts
with other libraries you may be using that incidentally also extend the same
type with an identically named method and signature. This happened with
MoreLINQ, for example, when Microsoft .NET Framework 4.0 introduced
[`Zip`][netzip] and [MoreLINQ already had one][zip]. Starting with version 2.4
of MoreLINQ, you reduce the potential for present (or even future) conflicts
by individually importing just the extension methods you need using the
[static imports feature introduced in C# 6][using-static]:

```c#
using static MoreLinq.NoConflict.LagExtension;
using static MoreLinq.NoConflict.LeadExtension;
```

In the example above, only the [`Lag`][lag] and [`Lead`][lead] extension
methods will be available in scope.

Apart from extension methods, MoreLINQ also offers regular static method
that *generate* (instead of operating on) sequences, like `Unfold`,
`Random`, `Sequence` and others. If you want to use these while statically
importing other individual extension methods, you can do so via aliasing:

```c#
using static MoreLinq.NoConflict.LagExtension;
using static MoreLinq.NoConflict.LeadExtension;
using MoreEnumerable = MoreLinq.MoreEnumerable;
```

In the example above, [`Lag`][lag] and [`Lead`][lead] will be available as
extension methods as well as all the regular static methods on
`MoreEnumerable` but _without_ any of the extension methods offered by
`MoreEnumerable`.


[lag]: https://morelinq.github.io/2.0/ref/api/html/Overload_MoreLinq_MoreEnumerable_Lag.htm
[lead]: https://morelinq.github.io/2.0/ref/api/html/Overload_MoreLinq_MoreEnumerable_Lead.htm
[using-static]: https://docs.microsoft.com/en-us/dotnet/articles/csharp/whats-new/csharp-6#using-static
[netzip]: https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.zip--3
[zip]: https://morelinq.github.io/2.0/ref/api/html/M_MoreLinq_MoreEnumerable_Zip__3.htm
[unfold]: https://morelinq.github.io/2.3/ref/api/html/M_MoreLinq_MoreEnumerable_Unfold__3.htm
[random]: https://morelinq.github.io/2.0/ref/api/html/Overload_MoreLinq_MoreEnumerable_Random.htm
[sequence]: https://morelinq.github.io/2.2/ref/api/html/Overload_MoreLinq_MoreEnumerable_Sequence.htm


## Operators

### Acquire

Ensures that a source sequence of objects are all acquired successfully. If
the acquisition of any one fails then those successfully acquired till that
point are disposed

### AggregateRight

Applies a right-associative accumulator function over a sequence.
This operator is the right-associative version of the Aggregate LINQ operator.

This method has 3 overloads.

### Assert

Asserts that all elements of a sequence meet a given condition otherwise
throws an object.

This method has 2 overloads.

### AssertCount

Asserts that a source sequence contains a given count of elements.

This method has 2 overloads.

### AtLeast

Determines whether or not the number of elements in the sequence is greater 
than or equal to the given integer.

### AtMost

Determines whether or not the number of elements in the sequence is lesser 
than or equal to the given integer.

### Batch

Batches the source sequence into sized buckets.

This method has 2 overloads.

### Cartesian

Returns the Cartesian product of two sequences by combining each element of
the first set with each in the second and applying the user=define projection
to the pair

### Concat

Returns a sequence consisting of the head element and the given tail elements.

This method has 2 overloads.

### Consume

Completely consumes the given sequence. This method uses immediate execution,
and doesn't store any data during execution

### CountBetween

Determines whether or not the number of elements in the sequence is between an 
inclusive range of minimum and maximum integers.

### CountBy

Applies a key-generating function to each element of a sequence and returns a
sequence of unique keys and their number of occurrences in the original
sequence.

This method has 2 overloads.

### DistinctBy

Returns all distinct elements of the given source, where "distinctness" is
determined via a projection and the default equality comparer for the
projected type.

This method has 2 overloads.

### EquiZip

Returns a projection of tuples, where each tuple contains the N-th element
from each of the argument sequences.

This method has 3 overloads.

### Exactly

Determines whether or not the number of elements in the sequence is equals 
to the given integer.

### ExceptBy

Returns the set of elements in the first sequence which aren't in the second
sequence, according to a given key selector.

This method has 2 overloads.

### Exclude

Excludes elements from a sequence starting at a given index

### FallbackIfEmpty

Returns the elements of a sequence and falls back to another if the original
sequence is empty.

### FillBackward

Returns a sequence with each null reference or value in the source replaced
with the following non-null reference or value in that sequence.

This method has 3 overloads.

### FillForward

Returns a sequence with each null reference or value in the source replaced
with the previous non-null reference or value seen in that sequence.

This method has 3 overloads.

### Fold

Returns the result of applying a function to a sequence of 1 element.

This method has 4 overloads.

### ForEach

Immediately executes the given action on each element in the source sequence.

This method has 2 overloads.

### FullGroupJoin

Performs a Full Group Join between the and sequences.

This method has 2 overloads.

### Generate

Returns a sequence of values consecutively generated by a generator function

### GenerateByIndex

Returns a sequence of values based on indexes

### GroupAdjacent

Groups the adjacent elements of a sequence according to a specified key
selector function.

This method has 4 overloads.

### ~~Incremental~~

Use `Pairwise` instead, which is identical to `Incremental`. `Incremental`
will be removed in a future version.

Computes an incremental value between every adjacent element in a sequence:
{N,N+1}, {N+1,N+2}, .

This method has 2 overloads.

### Index

Returns a sequence of where the key is the zero-based index of the value in
the source sequence.

This method has 2 overloads.

### Interleave

Interleaves the elements of two or more sequences into a single sequence,
skipping sequences as they are consumed.

This method has 2 overloads.

### Lag

Produces a projection of a sequence by evaluating pairs of elements separated
by a negative offset.

This method has 2 overloads.

### Lead

Produces a projection of a sequence by evaluating pairs of elements separated
by a positive offset.

This method has 2 overloads.

### MaxBy

Returns the maximal element of the given sequence, based on the given
projection.

This method has 2 overloads.

### MinBy

Returns the minimal element of the given sequence, based on the given
projection.

This method has 2 overloads.

### NestedLoops

Produces a sequence from an action based on the dynamic generation of N nested
loops who iteration counts are defined by

### OrderBy

Sorts the elements of a sequence in a particular direction (ascending,
descending) according to a key.

This method has 2 overloads.

### OrderedMerge

Merges two ordered sequences into one. Where the elements equal in both
sequences, the element from the first sequence is returned in the resulting
sequence.

This method has 7 overloads.

### Pad

Pads a sequence with default values if it is narrower (shorter in length) than
a given width.

This method has 3 overloads.

### Pairwise

Returns a sequence resulting from applying a function to each element in the
source sequence and its predecessor, with the exception of the first element
which is only returned as the predecessor of the second element

### Permutations

Generates a sequence of lists that represent the permutations of the original
sequence

### Pipe

Executes the given action on each element in the source sequence and yields it

### Prepend

Prepends a single value to a sequence

### PreScan

Performs a pre-scan (exclusive prefix sum) on a sequence of elements

### Random

Returns an infinite sequence of random integers using the standard .NET random
number generator.

This method has 6 overloads.

### RandomDouble

Returns an infinite sequence of random double values between 0.0 and 1.0.

This method has 2 overloads.

### RandomSubset

Returns a sequence of a specified size of random elements from the original
sequence.

This method has 2 overloads.

### Rank

Ranks each item in the sequence in descending ordering using a default
comparer.

This method has 2 overloads.

### RankBy

Ranks each item in the sequence in descending ordering by a specified key
using a default comparer.

This method has 2 overloads.

### Repeat

Repeats the sequence indefinitely or a specific number of times.

This method has 2 overloads.

### RunLengthEncode

Run-length encodes a sequence by converting consecutive instances of the same
element into a `KeyValuePair<T, int>` representing the item and its occurrence
count.

This method has 2 overloads.

### Scan

Peforms a scan (inclusive prefix sum) on a sequence of elements.

This method has 2 overloads.

### Segment

Divides a sequence into multiple sequences by using a segment detector based
on the original sequence.

This method has 3 overloads.

### Sequence

Generates a sequence of integral numbers within the (inclusive) specified range.

This method has 2 overloads.

### ~~SingleOrFallback~~

Consider using `FallbackIfEmpty` instead. `SingleOrFallback` may be removed in
a future version. For more information, see issue [#122][#122].

Returns the single element in the given sequence, or the result of executing a
fallback delegate if the sequence is empty. This method throws an exception if
there is more than one element in the sequence

### SkipLast

Bypasses a specified number of elements at the end of the sequence.

### SkipUntil

Skips items from the input sequence until the given predicate returns true
when applied to the current source item; that item will be the last skipped

### Slice

Extracts elements from a sequence at a particular zero-based starting index

### SortedMerge

Merges two or more sequences that are in a common order (either ascending or
descending) into a single sequence that preserves that order.

This method has 2 overloads.

### Split

Splits the source sequence by a separator.

This method has 12 overloads.

### Subsets

Returns a sequence of representing all of the subsets of any size that are
part of the original sequence.

This method has 2 overloads.

### TagFirstLast

Returns a sequence resulting from applying a function to each element in the
source sequence with additional parameters indicating whether the element is
the first and/or last of the sequence

### TakeEvery

Returns every N-th element of a source sequence

### TakeLast

Returns a specified number of contiguous elements from the end of a sequence

### TakeUntil

Returns items from the input sequence until the given predicate returns true
when applied to the current source item; that item will be the last returned

### ThenBy

Performs a subsequent ordering of elements in a sequence in a particular
direction (ascending, descending) according to a key.

This method has 2 overloads.

### ToDataTable

Appends elements in the sequence as rows of a given object with a set of
lambda expressions specifying which members (property or field) of each
element in the sequence will supply the column values.

This method has 4 overloads.

### ToDelimitedString

Creates a delimited string from a sequence of values. The delimiter used
depends on the current culture of the executing thread.

This method has 30 overloads.

### TraverseBreadthFirst

Traverses a tree in a breadth-first fashion, starting at a root node and using
a user-defined function to get the children at each node of the tree.

### TraverseDepthFirst

Traverses a tree in a depth-first fashion, starting at a root node and using a
user-defined function to get the children at each node of the tree.

### ToHashSet

Returns a of the source items using the default equality comparer for the
type. 

This method has 2 overloads.

### PartialSort

Combines `OrderBy` (where element is key) and `Take` in a single operation.

### PartialSortBy

Combines `OrderBy` and `Take` in a single operation.

### Trace

Traces the elements of a source sequence for diagnostics.

This method has 3 overloads.

### Unfold

Returns a sequence generated by applying a state to the generator function, 
and from its result, determines if the sequence should have a next element and 
its value, and the next state in the recursive call.

This method has 2 overloads.

### Windowed

Processes a sequence into a series of subsequences representing a windowed
subset of the original

### ZipLongest

Returns a projection of tuples, where each tuple contains the N-th element
from each of the argument sequences

### ZipShortest

Returns a projection of tuples, where each tuple contains the N-th element
from each of the argument sequences.

This method has 3 overloads.


[#122]: https://github.com/morelinq/MoreLINQ/issues/122
