
+++
title = "(Optional) Break & Continue"
date = 2020-08-29T16:56:21-07:00
weight = 80
+++


`break` and `continue` allow you to control the flow of your loops. They're a concept that beginners to Python tend to misunderstand.

{{% notice info %}}
This chapter won't be covered in the course, but I recommend you bookmark it and come back to it later.
{{% /notice %}}

### Using `break`

The `break` statement will completely break out of the *current loop*, meaning it won't run any more of the statements contained inside of it.


```python
>>> names = ["Rose", "Max", "Nina", "Phillip"]
>>> for name in names:
...     print(f"Hello, {name}")
...     if name == "Nina":
...         break
...
Hello, Rose
Hello, Max
Hello, Nina
```

{{% notice tip %}}
`break` completely **breaks out** of the loop.
{{% /notice %}}

### Using `continue`

`continue` works a little differently. Instead, it goes back to the start of the loop, skipping over any other statements contained within the loop.

```python
>>> for name in names:
...     if name != "Nina":
...         continue
...     print(f"Hello, {name}")
...
Hello, Nina
```

{{% notice tip %}}
`continue` continues to the **start of the loop**

{{% /notice %}}


### `break` and `continue` visualized

What happens when we run the code from this Python file?

```python
# Python file names.py
names = ["Jimmy", "Rose", "Max", "Nina", "Phillip"]

for name in names:
    if len(name) != 4:
        continue

    print(f"Hello, {name}")

    if name == "Nina":
        break

print("Done!")
```

![break and continue visualized](/images/break-continue.png?classes=shadow,border)

#### Results

{{%expand "See if you can guess the results before expanding this section." %}}
```bash
(env) $ python names.py

Hello, Rose
Hello, Nina
Done!
```
{{% /expand%}}

### Using `break` and `continue` in nested loops.

Remember, `break` and `continue` only work for the **current loop**. *Even though I've been programming Python for years, this is something that still trips me up!*

```python
>>> names = ["Rose", "Max", "Nina"]
>>> target_letter = 'x'
>>> for name in names:
...     print(f"{name} in outer loop")
...     for char in name:
...             if char == target_letter:
...                 print(f"Found {name} with letter: {target_letter}")
...                 print("breaking out of inner loop")
...                 break
...
Rose in outer loop
Max in outer loop
Found Max with letter: x
breaking out of inner loop
Nina in outer loop
>>>
```

{{% notice tip %}}
`break` in the inner loop only breaks out of the inner loop! The outer loop continues to run.
{{% /notice %}}


### Loop Control in `while` loops

You can also use `break` and `continue` in `while` loops. One common scenario is running a loop forever, until a certain condition is met.

```python
>>> count = 0 
>>> while True:
...     count += 1
...     if count == 5:
...             print("Count reached")
...             break
...
Count reached
```

{{% notice note %}}
Be careful that your condition will eventually be met, or else your program will get stuck in an infinite loop. For production use, it's better to use asynchronous programming.
{{% /notice %}}

