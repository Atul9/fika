<img src="https://github.com/fika-lang/assets/blob/master/logo.png?raw=true" width="150"/> 

Fika is a modern programming language for the web.
It is statically typed, functional and runs on the BEAM (Erlang VM).
Fika is designed for building and maintaining scalable web apps without
compromising on programmer ergonomics.

### Syntax

Here's a quick walkthrough of Fika's syntax.

#### Functions

A function in Fika looks like this:

```elixir
# example.fi
fn sum(a: Int, b: Int) : Int do
  a + b
end
```

This is a function named `sum` which takes two integers and returns another integer.
Identifiers in Fika are written in snake_case (similar to Ruby, Elixir or Python).
Types are written in CamelCase.

Fika has a type checker which makes sure your function actually return what
they say they do. For example, the type checker will report an error for
the following code:

```elixir
fn sum(a: Int, b: Int) : Float do
  a + b
end

# Error: "Expected type: Float, got: Int"
```

All functions in Fika are nested inside modules.
Module names in Fika are inferred from their file paths, so a Fika file named
`example.fi` will become a module named `example`. All functions inside this
file will belong to this module.

The `sum` function can be called like so:

```elixir
# Calling locally within the module
sum(40, 2)

# Calling remotely outside the module
example.sum(40, 2)
```

#### Basic types and operators

Fika currently has only integers, variables, assignments and basic arithmetic
while it's still in the proof-of-concept stage. Here's how you assign
variables:

```elixir
a = 40
b = 2
c = sum(a, b)
```


### Running Fika programs

Fika is written in Elixir, so make sure you have that installed.
Follow [these instructions](https://elixir-lang.org/install.html) to install
Elixir.

```
# Clone and cd into fika, then run the following:
mix deps.get
iex -S mix

# In the elixir shell, compile and load a Fika file using the following:
> Fika.Code.load_file("example.fi")

# Now you can run functions from the module like this:
> :example.sum(40, 2)
> 42
```
