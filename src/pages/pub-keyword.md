# `pub` keyword

## Basic Usage

- `pub` makes a declaration publicly accessible from other files or modules
- Without `pub`, declarations are private by default

```zig
pub fn publicFunction() void {}
fn privateFunction() void {}
```

## Structs and Enums

- Use `pub` on struct/enum declarations and individual fields/variants

```zig
pub const MyStruct = struct {
    pub x: i32,
    y: i32, // private
};

pub const MyEnum = enum {
    pub A,
    B, // still public in enums
};
```

## Nested Declarations

- Each level needs its own `pub` for public access

```zig
pub const Outer = struct {
    pub const Inner = struct {
        pub fn foo() void {}
    };
};
```

## Modules

- Use `pub` for declarations to be accessible when the module is imported

## Test Functions

- Always public, even without `pub`

## Usingnamespace

- Re-export public declarations from another namespace

```zig
pub usingnamespace @import("other_module.zig");
```

## Comptime

- Use with comptime blocks for public compile-time declarations

```zig
pub comptime {
    const X: i32 = 10;
}
```

## Constants and Variables

- Use at global scope

```zig
pub const GLOBAL_CONSTANT: i32 = 42;
pub var global_variable: i32 = 0;
```

## Local Scopes

- No effect inside functions

## Packages

- Only `pub` declarations in the root source file are accessible to dependent packages

## Key Points

- Aligns with Zig's explicit philosophy
- No "protected" or "internal" access - only public or private
- Crucial for designing clean, secure APIs and maintaining encapsulation
