# Install

🌐 **English** · [Dansk](Install-da) · [Bahasa Melayu](Install-ms)

## Use the files directly

Nothing to install. Clone and open the checklist you need.

This repository is public, so HTTPS works without an account:

```bash
git clone https://git.tirsystem.com/TirSystem/sqa-qc-checklists.git
# or the read-only GitHub mirror
git clone https://github.com/TirSystem/sqa-qc-checklists.git
```

SSH works too, if you have access to `git.tirsystem.com`:

```bash
git clone ssh://git@git.tirsystem.com:10022/TirSystem/sqa-qc-checklists.git
```

The canonical repository is on `git.tirsystem.com`; the GitHub repository is a
read-only mirror.

## As a submodule of your project

```bash
git submodule add https://github.com/TirSystem/sqa-qc-checklists.git qc
git submodule update --init
```

Pin a commit or tag so your reviews are reproducible; update it with a
deliberate commit.

## With the SQA and QC Framework

You do not install this repository separately. The framework mounts it at
`framework/qc/` as a nested submodule:

```bash
git submodule update --init --recursive
```

If `framework/qc/` is empty, no review can start. See the
[framework Install page](https://git.tirsystem.com/TirSystem/sqa-qc-framework/wiki/Install).

## Contributing a change

A new or changed criterion is a release item. Change the checklist, add a
Version History row, and keep every criterion tagged with an ISO/IEC 25010
characteristic and a level.
