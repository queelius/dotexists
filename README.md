# `dotexists` - Existence Check for Nested Data Structures

> "To be, or not to be, that is the question."
>
> — William Shakespeare

**Check for the existence of a value in a nested data structure using an exact path.**

`dotexists` is the simplest tool in the **Logic Pillar** of the `dot` ecosystem. It asks one question: "Does this exact path exist in the data?" It returns `True` or `False`.

```python
>>> from dotexists import check
>>> data = {"user": {"name": "Alice", "address": None}}
>>> check(data, "user.name")
True
>>> check(data, "user.address")
True
>>> check(data, "user.age")
False
```

## The Logic Pillar vs. The Addressing Pillar

The `dot` ecosystem is divided into two philosophical pillars:

1.  **The Addressing Pillar (`dotget`, `dotstar`, `dotselect`):** Answers the question, **"What is the value?"** These tools return data.
2.  **The Logic Pillar (`dotexists`, `dotany`, `dotall`, `dotquery`):** Answers the question, **"Is it true?"** These tools return `True` or `False`.

`dotexists` is the logical counterpart to `dotget`. It provides the simplest possible truth check.

## Install

```bash
pip install dotexists
```

## Command-Line Usage

The `dotexists` CLI tool returns an exit code, making it perfect for shell scripting.

-   **Exit Code `0`:** The path exists.
-   **Exit Code `1`:** The path does not exist, or an error occurred.

```bash
# Check if 'user.name' exists in a JSON file
if cat data.json | dotexists "user.name"; then
    echo "User name exists!"
fi

# Check a YAML file
if dotexists "user.name" data.yaml; then
    echo "User name exists!"
fi
```

## Philosophy: The Simplest Truth

`dotexists` is the logical counterpart to `dotget`. It does one thing: check for the existence of a value at an exact path. It doesn't interpret the value, it only confirms its presence.

It is the foundation of the Logic Pillar, providing a clear, unambiguous, and philosophically pure tool for the most basic logical question you can ask of your data: "Is it there?"
