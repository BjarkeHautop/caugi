# Register a new edge type in the global registry.

Register a new edge type in the global registry.

## Usage

``` r
register_caugi_edge(glyph, tail_mark, head_mark, class, symmetric = FALSE)
```

## Arguments

- glyph:

  A string representing the edge glyph (e.g., `"-->"`, `"<->"`).

- tail_mark:

  One of "arrow", "tail", "circle", "other".

- head_mark:

  One of "arrow", "tail", "circle", "other".

- class:

  One of "directed","undirected","bidirected","partial".

- symmetric:

  Logical.

## Value

TRUE, invisibly.

## See also

Other registry:
[`registry`](https://caugi.org/dev/reference/registry.md)

## Examples

``` r
# first, for reproducability, we reset the registry to default
reset_caugi_registry()

# create a new registry
reg <- caugi_registry()

# list registered edges
list_caugi_edges()
#>   glyph   tail   head                class symmetric
#> 1   -->   tail  arrow             directed     FALSE
#> 2   ---   tail   tail           undirected      TRUE
#> 3   <->  arrow  arrow           bidirected      TRUE
#> 4   o-o circle circle              partial      TRUE
#> 5   --o   tail circle partially_undirected     FALSE
#> 6   o-> circle  arrow   partially_directed     FALSE

# register an edge
register_caugi_edge(
  glyph = "<--",
  tail_mark = "arrow",
  head_mark = "tail",
  class = "directed",
  symmetric = FALSE
)

# now, this edge is available for caugi graphs:
list_caugi_edges()
#>   glyph   tail   head                class symmetric
#> 1   -->   tail  arrow             directed     FALSE
#> 2   ---   tail   tail           undirected      TRUE
#> 3   <->  arrow  arrow           bidirected      TRUE
#> 4   o-o circle circle              partial      TRUE
#> 5   --o   tail circle partially_undirected     FALSE
#> 6   o-> circle  arrow   partially_directed     FALSE
#> 7   <--  arrow   tail             directed     FALSE
cg <- caugi(A %-->% B, B %<--% C, class = "DAG")

# reset the registry to default
reset_caugi_registry()
```
