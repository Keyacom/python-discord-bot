---
aliases: ["slice", "seqslice", "seqslicing", "sequence-slice", "sequence-slicing"]
embed:
    title: "Sequence slicing"
---
You're trying to get a part of a string, list, or another sequence object, but you don't want to use manual incrementing (which may be prone to errors)? There comes the need to *slice* it.

There is a special syntax that can be used to slice a given `some_seq` sequence: `some_seq[i:j:k]`, where `i` is the starting index, `j` is the end index, and `k` is the step, i.e. every how many items should one be kept. If any of these values are missing, they're assumed as `some_seq[0:len(some_seq):1]`.

The brackets must have at least at least a colon (cannot be empty). Using just an int as the subscription will return only one item. Using just `[:]` or `[::]` (without any numbers) will return a *copy* of the iterable if it's a `list` or a `bytearray`, reducing the need for the `copy()` method.

**Examples**

```py
>>> l = [1, 2, 3, 4]
>>> l[2:]
[3, 4]
>>> l[:2]
[1, 2]
>>> assert l[:2] + l[2:] == l
>>> l[::-1]
[4, 3, 2, 1]
>>> assert list(reversed(l)) == l[::-1]
>>> l[:]
[1, 2, 3, 4]
>>> l[::2]
[1, 3]
>>> from random import randint
>>> for i in range(10):
...     x, y = randint(0, len(l)), randint(0, len(l))
...     assert len(l[x:y]) <= len(l)
```

Additionally, using `some_list[::-1]` is the same as `list(reversed(some_list))`. Just like in regular sequence subscriptions, negative numbers may be used.

**Note**
If the start index is greater than the end index, the resulting sequence will be empty.
