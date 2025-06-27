# `dotexists`: Simple Existence Check

> "To be, or not to be, that is the question."
>
> — William Shakespeare

**Check for the existence of a value in a nested data structure using a precise path.**

`dotexists` is the simplest tool in the **Logic Pillar** of the `dot` ecosystem. It asks one question: "Does this exact path exist in the data?" It returns `True` or `False` and is the logical counterpart to `dotget`.

```python
>>> from dotexists import check
>>> data = {"user": {"name": "Alice", "address": None}}
>>> check(data, "user.name")
True
>>> check(data, "user.address") # Note: None is an existing value
True
>>> check(data, "user.age")
False
```

## The Philosophy: The Simplest Truth

The `dot` ecosystem is divided into two pillars:

1.  **The Addressing Pillar (`dotget`, `dotstar`, `dotselect`):** Answers the question, **"What is the value at this address?"** These tools find and return data.
2.  **The Logic Pillar (`dotexists`, `dotany`, `dotall`, `dotquery`):** Answers the question, **"Is this statement about the data true?"** These tools return a boolean result.

`dotexists` is the foundation of the Logic Pillar. It performs the most basic check possible. For any more complex question—such as checking a value, using wildcards, or applying quantifiers like `any` or `all`—you should use `dotquery`.

- **`dotexists`:** Does `user.0.name` exist?
- **`dotquery`:** Do `any` users have the role `admin`?

## Install

```bash
pip install dotexists
```

## Command-Line Usage

The `dotexists` CLI tool is perfect for shell scripting. It reads JSON from stdin or a file and returns an exit code:

-   **Exit Code `0`:** The path exists.
-   **Exit Code `1`:** The path does not exist.

```bash
# Check if 'user.name' exists in a JSON file
if cat data.json | dotexists "user.name"; then
    echo "User name exists!"
fi

# Check a YAML file by providing it as an argument
if dotexists "user.name" data.yaml; then
    echo "User name exists!"
fi
```

## Boundaries: When to Use `dotexists`

Use `dotexists` when you need to:
✅ Verify that a specific, required key is present in configuration.
✅ Guard a `dotget` call in a script.
✅ Perform the simplest possible truth check on a data structure.

Do **not** use `dotexists` when you need to:
❌ Check if a value matches a certain condition. **Use `dotquery`**.
❌ Check if `any` or `all` items in a list match a path. **Use `dotquery`**.
❌ Get the value itself. **Use `dotget`**.
