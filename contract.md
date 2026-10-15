# HEATWAVE reserve contract

This page accompanies the exact Rust contract source, pinned Cargo dependencies and isolated runtime tests used by HEATWAVE. See [the reserve transparency page](reserve-and-transparency.md) for the verified Mainnet program, configuration, initial funding and immutable-authority transactions.

The source has three instructions: initialize, register_player and claim. It contains no administrator withdrawal or replacement-key path. Claims require a player and the configured game backend; the backend remains trusted to authorize genuine gameplay earnings. No independent security audit is claimed.

## Snapshot and build limits

[SOURCE-SNAPSHOT.json](SOURCE-SNAPSHOT.json) records the source-file SHA-256 alongside the separately verified 210,168-byte deployed ELF hash. Source and ELF hashes are different measurements. Public source plus a recorded binary hash does not establish an independently reproduced build.

Files are copied without changing the published source bytes. Some source comments and the Cargo package description retain pre-deployment wording; deployment status is documented by the transaction evidence, not those historical comments. No new license grant is asserted here; dependency license metadata remains in its original files and packages.

## Build and tests

The individual files below are flat browsing copies. Their names are adapted for a single GitHub upload; their source and dependency bytes are unchanged. Use [contract-source.zip](contract-source.zip) for the original directory layout and filenames. It contains the complete contract directory with source, pinned build dependencies and isolated runtime tests.

| Browse the published copy | Path inside the ZIP |
| --- | --- |
| [Rust source](reserve-program.rs) | contract/src/lib.rs |
| [Cargo manifest](reserve-Cargo.toml) | contract/Cargo.toml |
| [Cargo lockfile](reserve-Cargo.lock) | contract/Cargo.lock |
| [Runtime tests](reserve.runtime.test.mjs) | contract/tests/reserve.runtime.test.mjs |
| [Test package manifest](reserve-tests-package.json) | contract/tests/package.json |
| [Test package lockfile](reserve-tests-package-lock.json) | contract/tests/package-lock.json |

The recorded toolchain uses Anchor 1.1.2, Agave 4.3.0 and Anza platform-tools 1.58 with SBPFv3. Download the ZIP and extract it on a supported Linux development host. The following commands enter its preserved contract directory before building:

```sh
unzip contract-source.zip
cd contract
NO_DNA=1 CARGO_TARGET_DIR=/path/to/isolated-target cargo test --locked
NO_DNA=1 CARGO_PROFILE_RELEASE_OPT_LEVEL=z cargo-build-sbf --manifest-path Cargo.toml --tools-version v1.58 --arch v3 --sbf-out-dir /path/to/isolated-artifacts -- --locked
cd tests
npm ci --ignore-scripts --no-audit --no-fund
HTW_RESERVE_SBF=/path/to/isolated-artifacts/heatwave_protected_reserve.so npm test
```

Runtime tests use temporary in-memory keys and an isolated LiteSVM instance. They do not call Mainnet or require a wallet/private key. Missing artifacts or native dependencies must fail the test setup. These tests check signatures, replay, account substitution, token/SOL fee arithmetic, time/holding/backing gates and rollback; they are not a guarantee that no defects remain.

Do not run deployment commands or send tokens to an address merely to reproduce local tests. Public hosting readiness and real-player workflow verification are separate from contract build verification.
