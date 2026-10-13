# Module System

This page explains how software modules are managed on Aire and Calder, with a focus on the differences between their module systems. For basic instructions on finding and loading software, start with [Software on HPC](../software/start.md) and browse the relevant software pages.

## What are environment modules?

The HPC systems use an *environment module* system to manage centrally installed software. Modules let users select different applications and versions without having to manually configure their environments. They also help ensure that centrally installed software is configured for the system and reduce conflicts between applications and libraries.

The Research Computing team installs and maintains commonly used software centrally. If software would be useful to multiple users, you can [request a new software installation](page:request-software). Requests are assessed for suitability as a shared application. Most open-source software can be incorporated, and commercial software may be supported where suitable licences are available.

## Differences between Aire and Calder

Aire's current module system is **flat**: `module avail` lists the modules available in the current module path.

Calder uses a **hierarchical** module system. The software visible to you depends on the CPU or GPU environment and, where applicable, the compiler or MPI stack that you have loaded. As a result, `module avail` may show only a small number of top-level environments until you load one.

The current Aire system and Calder therefore have different software discovery and loading workflows. Aire 2.0 is planned to introduce a hierarchical module system similar to Calder.

## Calder's module hierarchy

### Recommended module configuration

After logging in to Calder, please set the module path to use Calder's software stack:

```bash
export MODULEPATH=/uol/apps/calder/modules
```

This reduces the likelihood of accidentally loading software from another system and helps ensure you are using the intended Calder software environment.

:::{note}
Integration of the software environments across Aire and Calder is ongoing, so the separation between them is not yet fully refined.

Calder modules remain available even if you do not modify `MODULEPATH`. However, you may see software from multiple environments, which can make it harder to determine which module is being loaded. We recommend setting `MODULEPATH` as shown above to avoid this confusion.
:::

### Understanding the hierarchy

To view the top-level environments available on Calder, run:

```bash
module avail
```

The output should look similar to:

```text
------------- /uol/apps/calder/modules ------------

calder/cpu calder/hopper
```

The top-level environments include:

- `calder/cpu` - software environment for CPU workloads.
- `calder/hopper` - software environment for workloads using Calder's GPU nodes.

Load the environment that matches your workload to make additional software available. For example, to view software built for the CPU environment, run:

```bash
module load calder/cpu
module avail
```

For the Hopper GPU environment, run:

```bash
module load calder/hopper
module avail
```

Loading compiler, MPI or other software modules may expose further layers of compatible software in the hierarchy.

### Searching the full module hierarchy

`module avail` shows modules visible in the currently active layer. To search across the full module tree, use:

```bash
module spider
```

To find the loading instructions and prerequisites for a particular package, run:

```bash
module spider <module-name>
```

For example:

```bash
module spider openfoam
```

The output describes the available versions and any prerequisite modules or loading sequence required to use the software.

For general instructions on loading a module and links to available software, see [Software on HPC](../software/start.md).
