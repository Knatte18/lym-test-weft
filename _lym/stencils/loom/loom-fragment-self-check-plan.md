<!-- This is the Plan-Write prompt's self-check step body for a run whose plan gate has no cold fixer: the writer runs the validator itself.
     It is filled whole into loom-template-plan's self_check marker by internal/loomengine's PlanTable.
     It declares no marker.
lym-stencil: sha256=6174ec041abeb84d7ed376ccfbd28a6ba5230832fb5e252e55d7803006c2d156 build=f2ae537d965d3bd8ac0ed89d3acb54142f223693 time=2026-11-05T08:31:59Z -->

Before ending your turn, run the mechanical gate standalone against what you just wrote:

```bash
lym loom validate-plan
```

The verb takes no arguments.
It exits 0 on a clean gate and 1 otherwise, and puts its findings under the failure envelope's `findings` key.
Fix whatever it reports, then re-run it until it exits 0 before ending your turn.
