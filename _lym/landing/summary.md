# Add a standalone API greeting

The `services/api` package now has its own Go 1.22 module and a `Greeting` function that returns the supplied name in a greeting, defaulting blank or whitespace-only input to `world`.
The executable prints the default greeting, and a table-driven test covers named, empty, and whitespace-only input.
