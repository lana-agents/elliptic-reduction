# elliptic-reduction

Elliptic curve reduction theory beyond Mathlib.

## Goals

Develop the reduction theory needed to discharge the `ReductionCertificate` interface that IUT4 §1 keeps explicit for Proposition 1.8(v)–(vii).

In scope, none of which is packaged in Mathlib v4.32.0:

* semistable and Néron models;
* moduli with level structure;
* inertia actions;
* Galois descent for elliptic curves;
* Serre-type criteria via polarized abelian varieties and Tate modules.

This is a standalone arithmetic-geometry project. `iut` states the relevant results conditionally on the certificate; discharging it with real proofs happens here.

## Related repositories

Discharges a certificate interface used by `iut`. Distinct from `tate-curves-theta`, which concerns Tate uniformization and the theta function.

## Layout

Lean 4 project pinned to `leanprover/lean4:v4.32.0` with Mathlib at `v4.32.0`.
Library sources live under `EllipticReduction/`, and every file must be imported from
the root module `EllipticReduction.lean`.

```bash
lake exe cache get                       # fetch the Mathlib build cache
lake build                               # build the library
lake exe mk_all --lib EllipticReduction --git   # regenerate the root module after adding files
```

## Validation

`.orchestra/` tells the agent harness how to prepare the environment and how to
check that a change is complete:

* `before.sh` warms the Mathlib build cache before work starts.
* `validation.sh` checks the worktree is clean, that every `.lean` file is
  imported (`mk_all --check`), and that everything builds with warnings as
  errors (`lake build --wfail`).

Run it locally with `bash .orchestra/validation.sh`.

## Tracker

Work is tracked in taxis: [#5](https://taxis.lana.merten.dev/issues/5)
