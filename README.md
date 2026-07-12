# AIMind Releases

This public repository contains no application, Electron, Tauri, or packaging source code.

All desktop applications and installers are built in the private source repository. This repository only downloads finished, versioned release assets from the private repository and republishes them through public GitHub Releases.

## Repository contents

- Public release workflow
- Release metadata
- License
- Finished GitHub Release assets

## Required secret

- `PRIVATE_ARTIFACT_TOKEN`: fine-grained token with read-only Contents access to the private source repository.
