# Agent Skills

A portable [APM](https://github.com/microsoft/apm) manifest for frequently used Azure, .NET, and Karpathy agent skills.

## Install in another project

Copy [`apm.yml`](./apm.yml) into the root of your project, then run:

```sh
apm install --target claude,copilot
```

APM installs and integrates the dependencies for Claude Code and GitHub Copilot. The manifest pins each dependency to its upstream `main` branch.

## Included packages

- [Microsoft Azure skills](https://github.com/microsoft/azure-skills)
- [.NET skills](https://github.com/dotnet/skills): `dotnet`, `dotnet-aspnetcore`, and `dotnet-test`
- [Karpathy skills](https://github.com/multica-ai/andrej-karpathy-skills)
