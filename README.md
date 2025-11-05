# `csharp-editorconfig`
An opinionated `.editorconfig` ruleset for C#.

This ruleset is mostly equivalent to the standard .NET one, with the following changes:

## 1. Use kernel-style braces
By default, .NET formatting conventions place braces on their own lines for all blocks:

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

This ruleset instead applies **kernel-style formatting**, where braces for *definitions* (such as methods, classes, and namespaces) remain on their own lines, while braces for *control blocks* stay inline.

This creates a clear visual distinction between definitions and logic flow:

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
Most C# source files define only a single namespace. Indenting the entire file by one level in these cases adds unnecessary nesting and visual noise.

```cs
namespace Ascpixi.Example
{
    public static class Frobinator
    {
        public static void Frobinate()
        {
            Console.WriteLine("Frobinated!");
        }
    }    
}
```

We enforce **file-scoped namespaces** instead.

```cs
namespace Ascpixi.Example;

public static class Frobinator
{
    public static void Frobinate()
    {
        Console.WriteLine("Frobinated!");
    }
}
```

## 3. Enforce `this.` prefix on fields
Since private fields and local variables share the same naming convention, requiring the `this.` prefix for field access helps avoid ambiguity. This also makes field references explicit, which communicates programmer intent more clearly for new contributors.
