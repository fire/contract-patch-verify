# Vendored components and their licences

Every directory under `vendor/` keeps the licence text its upstream ships. This
file is the index; the authoritative text is the file beside the code.

Checked against [Google's third-party licence policy][policy]. Notice licences
ship anywhere with attribution; reciprocal ones ship but oblige source
mirroring; restricted ones taint what links them.

[policy]: https://opensource.google/documentation/reference/thirdparty/licenses

| component | upstream | licence | category |
|---|---|---|---|
| `Eigen` | libeigen/eigen | MPL-2.0, with BSD and MINPACK parts | reciprocal |
| `geogram` | BrunoLevy/geogram | BSD-3-Clause (Inria) | notice |
| `pmp` | pmp-library/pmp-library | MIT | notice |
| `cassie-triangulation` | fire/cassie-triangulation | MIT | notice |
| `slang-prelude` | shader-slang/slang | Apache-2.0 WITH LLVM-exception | notice |
| `lean-slang` | fire/lean-slang | see its own `LICENSE` | notice |
| `curve_rdp` | generated | Slang output, not vendored third-party source | — |

## Eigen carries no LGPL code here

Eigen's documentation warns that a few features rely on LGPL third-party code,
and `COPYING.README` still mentions it. That does not apply to this tree, which
was checked file by file rather than taken from the warning:

| file | licence |
|---|---|
| `src/OrderingMethods/Amd.h` | MPL-2.0, adapted from CSparse |
| `src/SparseCholesky/SimplicialCholesky_impl.h` | MPL-2.0, adapted from LDL |

Both carry Eigen's standard MPL-2.0 header and Timothy Davis's permissive notice,
and neither contains the string LGPL. This is Eigen 3.4.0, where those files are
MPL-2.0. The one genuinely LGPL file, `ConstrainedConjGrad.h`, lives under
`unsupported/`, and no `unsupported/` tree is vendored.

So `COPYING.LGPL` is deliberately **not** retained: no file here is under it, and
shipping the text would tell a reader — and any scanner — that LGPL code is
present when none is.

`-DEIGEN_MPL2_ONLY` is likewise not set. The macro appears nowhere in the 389
vendored Eigen files, so in 3.4.0 it would change nothing.

Eigen is MPL-2.0, which the policy classes as **reciprocal**: it ships, but the
obligation to make source available extends to the library itself and any
modification of it. This copy is unmodified, and the full source is here.
