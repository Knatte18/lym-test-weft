# Add a standalone API greeting executable

Give `services/api` its own Go module so it can build independently.
Add `Greeting`, which returns `Hello, <name>!` and defaults empty or whitespace-only names to `world`.
The executable prints the default greeting, and a table-driven test covers named, empty and whitespace names.
