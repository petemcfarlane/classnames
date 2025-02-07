# Classnames

A simple utility for conditionally joining class names together.

## Installation

The package can be installed as:

```elixir
def deps do
  [{:classnames, "~> 0.1.0"}]
end
```

## Usage

This module only has one public function: `Classnames.classnames/1`. Here are a few examples:

```elixir
classnames([:one])                       #=> "one"
classnames(["one"])                      #=> "one"
classnames([:one, :two])                 #=> "one two"
classnames([active: 1 == 1])             #=> "active"
classnames([active: 1 == 2])             #=> ""
classnames([:one, :two, active: 1 == 1]) #=> "one two active"
classnames([:one, :two, active: 1 == 2]) #=> "one two"
classnames([{:active, 1 == 1}])          #=> "active"
classnames([{:active, 1 == 2}])          #=> ""
classnames([:one, {:active, 1 == 1}])    #=> "one active"
classnames([:one, {:active, 1 == 2}])    #=> "one"
```

## Phoenix

If you want classnames to be accessible in your Phoenix templates:

```elixir
defmodule MyApp.Web do
  def view do
    quote do
      # ...
      use Classnames
      # ...
    end
  end
end
```
