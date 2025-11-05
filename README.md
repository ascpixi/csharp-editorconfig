# `csharp-editorconfig`
An opinionated `.editorconfig` ruleset for C#.

This ruleset is mostly equivalent to the standard .NET one, with the following changes:

## 1. Use kernel-style braces
The .NET formatting conventions enforce braces on their own lines, always:
```cs
void Example(int width, int height)
{
    if (condition)
    {
        for (int x = 0; x < width; x++)
        {
            for (int y = 0; y < height; y++)
            {
                Console.WriteLine($"({x}, {y})");
            }
        }
    }
}
```

This ruleset instead enforces **kernel-style formatting** for this case - only blocks that are *definitions* have braces on separate line. Visually, this creates a "container" for each defintion, while keeping control blocks terse:

```cs
void Example(int width, int height)
{
    if (condition) {
        for (int x = 0; x < width; x++) {
            for (int y = 0; y < height; y++) {
                Console.WriteLine($"({x}, ${y})");
            }
        }
    }
}
```

## 2. Enforce file-scoped namespaces
C# source files almost *always* only contain a single namespace. Adding one level indentation to the grand majority of every source file in a project is unnecessary.

## 3. Enforce `this.` prefix on fields
As private fields have the same naming convention as local variables, a `this.` prefix avoids the possibility of mistaking the two. The prefix also more clearly communicates the intent of a field access to new contributors.
