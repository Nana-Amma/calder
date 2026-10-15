# Software on HPC

We provide centrally managed software on Aire and Calder through the environment module system. Modules let you select the software and versions you need for your work. Available software and module commands may differ between the two systems, so check the relevant documentation before running your workloads.

## Finding and loading software

To get started, connect to the system you want to use and run the following commands in your terminal.

1. **Find available software:** Run `module avail` to list modules available in your current environment.
2. **Load a module:** Run `module load <module-name>` to make the software available in your session. Replace `<module-name>` with the name of the module you want to use.
3. **Check the software instructions:** Refer to the relevant software page for any additional setup or usage instructions.

On Calder, the module system is hierarchical. You may need to load a CPU or GPU environment before the software you need becomes visible. To search the full module hierarchy, use `module spider <module-name>`. For more information, see [Module System](../system/module_system.md).

The module system differs between Aire and Calder, so module names and loading instructions may not be the same on both systems.

## Using software on Calder

Calder uses a **hierarchical module system**, and we are adding software modules and their documentation to this site gradually.

If you cannot find software or a module on Calder that is available on Aire, **please continue using Aire for that workload for now**. We will release more Calder modules and documentation over time. If a particular package is important to your work, you can also contact us or [request new software](page:request-software).

## Software categories

Browse the documentation by category:

- [Applications](./applications/start) - Software applications for various tasks
<!-- - [Compilers](./compilers/start) - Compilers for a range of programming languages -->
- [Interpreters](./interpreters/start) - Interpreters for running scripts and programs
<!-- - [Libraries](./libraries/start) - Libraries for enhancing functionality and performance -->
- [Tools](./tools/start) - Useful system utilities and tools

The software available in each category may differ between Aire and Calder. Check the individual software pages for system-specific instructions.

## Software on Aire

For instructions on using software modules on the current Aire system, see the [Aire User Documentation](https://arcdocs.leeds.ac.uk/aire/software/start.html).

We are also preparing the upgrade to **Aire 2.0**, which will introduce a hierarchical module system. After the upgrade, we will gradually bring the software documentation for Aire 2.0 and Calder together on this site.

## Installing or requesting software

You may install software yourself in your home directory (`~`) where appropriate. If you think software would be useful as a centrally managed module, see [Requesting new software](page:request-software).

If you have questions about software availability or using modules, please contact the Research Computing team.
