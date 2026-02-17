1. Write a python function for this
```
input = [1,2,3,4,5,6]
output= {
	"even": [2, 4, 6],
	"odd": [1, 3, 5]
}

```
my attempt
```
def split_list(input[]):
	# dictionary initialization
	# TODO
	for i in input:
		if i % 2 = 0:
			dict["even"].append(i)
		else:
			dict["odd"].append(i)
```

correct answer
```
def split_list(nums):
	result = {"even": [], "odd": []}
	
	for i in nums:
		if i % 2 == 0:
			result["even"].append(i)
		else:
			result["odd"].append(i)
	
	return result
```

more pythonic way
```
def split_list(nums):
	return {
		"even": [x for x in nums if x % 2 == 0],
		"odd": [x for x in nums if x % 2 != 0]
	}
```

2. write python function that returns the first non-repeating character across all strings combined

```
input = ["apple", "banana", "avocado"]
combined = "applebananaavocado"
output = "l"
```

My attempt
```
def non_repeating_character(var):
	for i,var[i] in enumerate(var):
		dict = {var : count(i)}
	
	return dict
```

Answer
```
def non_repeating_character(strings):
	combined = "".join(strings)
	freq = {}
	
	for ch in combined:
		freq[ch] = freq.get(ch, 0) + 1
		
	for ch in combined:
		if freq[ch] == 1:
			return ch
	
	return None
```

Pythonic alternative
```
from collections import Counter

def non_repeating_character(strings):
	combined = "".join(strings)
	counts = Counter(combined)
	
	for ch in combined:
		if counts[ch] == 1:
			return ch
	return None
```

3. Write a function that  takes a list of integers and returns True if any value appears at least twice.

My attempt
```
from collections import Counter

value_appears_twice(integers):
	counts = Counter(integers)
	
	for integer in counts:
		if counts[integer] > 2:
			return True
		else return False	
```

Correct Version
```
from collections import Counter

def value_appears_twice(integers):
	counts = Counter(integers)
	
	for integer in counts:
			if counts[integer] >= 2:
				return True
	return False
```

Even Better (Cleaner)
```
from collections import Counter

def value_appears_twice(integers):
	counts = Counter(integers)
	return any(count >= 2 for count in counts.values())
```

Interviewers prefer this O(n) Approach
```
def value_appears_twice(integers):
	seen = set()
	
	for num in integers:
		if num in seen:
			return True
		seen.add(num)
		
	return False
```

4. Write a function that returns the length of the longest substring without repeating characters.

```
input = "abcabcbb"
output = 3   # "abc"
```

My attempt
```
def longest_substring(string)
	seen = set()
	for i, ch in enumerate(string):
		if ch in seen:
			return i
		else:
			seen.add(ch)
```

Correct Solution
```
def longest_substring(s):
	seen = set()
	left = 0
	max_length = 0
	
	for right in range(len(s)):
		while s[right] in seen:
			seen.remove(s[left])
			left += 1
			
		seen.add(s[right])
		max_length = max(max_length, right - left + 1)
		
	return max_length
```

4a. Explain: Why do we use `while` instead of `if` here?
```
while s[right] in seen:
	seen.remove(s[left])
	left += 1
```

Perfect. Saying _“I don’t know”_ is 100× better than guessing in interviews 👍  
Now let’s understand it properly.

---

## 🔥 Why `while` and NOT `if`?

This line:

```python
while s[right] in seen:
    seen.remove(s[left])
    left += 1
```

### The key idea:

When we see a duplicate, we don’t know **where** the previous duplicate is inside the window.

We must keep shrinking the window **until the duplicate is removed**.

---

## 🔎 Example That Breaks `if`

Input:

```python
"abba"
```

Step-by-step:

### Iteration:

Window grows:

```
a → ab
```

Now at index 2:

```
"abb"
```

Duplicate `'b'` found.

If we use `if`:

```python
if s[right] in seen:
    seen.remove(s[left])
    left += 1
```

We remove only one character (`'a'`).

Window becomes:

```
"bb"
```

But duplicate `'b'` is still there ❌

So window is still invalid.

---

### Using `while`

```python
while s[right] in seen:
```

We keep removing from left:

Remove `'a'`  
Still duplicate

Remove `'b'`  
Now duplicate gone

Window becomes:

```
"b"
```

Now safe to continue.

---

## 💡 Core Insight

`if` removes only once  
`while` removes **until condition becomes false**

Sliding window problems almost always need `while`.

---

## 🧠 Interview-Level Understanding

Use `while` because:

> The window may contain multiple characters before the duplicate, and we must shrink the window completely until it becomes valid again.

---

5. Instead of using a `set`, optimize it using a dictionary so we don't remove characters one by one.
6. 