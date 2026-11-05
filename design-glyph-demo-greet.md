# Add and rename a greeting helper in services/api

`glyph-demo-greet` · Task · enhancement · draft

In services/api/main.go, add a new exported helper function in that same package that builds and returns a short greeting string (e.g. given a name, returns a greeting message). Update main() to call this new helper so it is actually used (printing the result is fine). Once that is in place, rename the helper to a more descriptive name that better reflects what it does. Keep the change minimal and scoped to services/api -- no new files or packages needed beyond what main.go already has, unless a bundled test file is appropriate for the new helper.