<!-- This is the Claude engine's copy of the background-command engine block:
     how a session on Claude runs a long lym command and learns that it ended.
     A stencil pulls it in after "Run `lym …`" with {{template "engine-background-command"}}.
     internal/stencilstore reads it for the launch's engine.
     It declares no marker.
lym-stencil: sha256=9fb6d932dfdb6f0a934ecc880f0fe4ed1b0d1a374f1838a6dc516b2aed5cdadc build=2bc62d626810d8eb25759e08749fa2a1a411e4bc time=2026-11-27T15:03:55Z -->
as a **backgrounded** Bash command, never in the foreground, end your turn, and act on the command's completion notification
