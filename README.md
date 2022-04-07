# algorithm_notes
This repo consists of the summeries of some useful algorithms.

## Monotonic stacks

### Monotonic increasing stacks

Since the stack we maintain is increasing, we can use it to find the smaller elements

1. previous less element - set the ple of the current iterator right before we insert the current iterator into the monotonic increasing stack
```
PLE = {}
stack = []
for i in l:
	while len(stack) and stack[-1] > i:
		stack.pop()
	PLE[i] = -1 if not len(stack) else stack[-1]
	stack.append(i) 
```
2. next less element - everytime when we need to pop from the stack, it means the iterable is less than the top of the stack, hence the NLE of the stack top is the current iterator. 
```
NLE = {}
stack = []
for i in l:
	while len(stack) and stack[-1] > i:
		x = stack.pop()
		NLE[x] = i
	stack.append(i)
```

### Monotonic decreasing stack

Similar as monotonic increasing stack, we use monotonic decreasing stack to find greater element.

1. previous greater element - right before we push the current iterator into the stack,
we mark the previous greater element of the current iterator as the top of the stack
```
PGE = {}
stack = []
for i in l:
	while len(stack) and stack[-1] < i:
		stack.pop()
	PGE[i] = -1 if not len(stack) else stack[-1]
	stack.append(i)
```

2. next greater element - everytime we need to pop out a value from the stack, it means this element is smaller than the current iterators, hence next greater element of the poped element is the current iterator.

```
NGE = {}
stack = []
for i in l:
	while len(stack) and stack[-1] < i:
		x = stack.pop()
		NGE[x] = i
	stack.append(i)
```
