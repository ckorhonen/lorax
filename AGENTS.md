# Repository agent guide

## Repository workflow and completion

Rust `router/` and `launcher/`, Python `server/`, and `clients/python/` have separate validation. Use pinned Rust 1.83 and Cargo.lock. Read Make targets: rust-tests installs binaries first; server installation generates protobuf code, installs Torch/dependencies, and may build GPU kernels. Python server support starts at 3.9, with material CUDA/PyTorch prerequisites.

Use focused Cargo tests after prerequisites. In `server/`, unit-tests runs `pytest -s -vv -m "not private" tests`; this excludes private tests but does not guarantee no GPU/download needs. Client/integration tests are separate. Do not start inference, download models, run GPU jobs, or change serving config as a prose check. Separate component coverage from inspected inference output.

Continue the authorized change through relevant validation and repair of failures it causes; preserve unrelated work. Report checks actually run, commands only inspected, and exact missing prerequisites. Ask only when a material decision, missing authorization, or required input blocks progress; continue independent reversible work. Existing mandatory contribution and validation gates still apply.
