# Vina Fork with Smina Optimization

This is a custom fork of **AutoDock Vina**, integrating the `minimize` method from **Smina** to improve docking optimization.

## Why this fork?

AutoDock Vina uses a quasi-Newton (BFGS) algorithm for local optimization during docking. However, testing revealed that it sometimes fails to converge to nearby energy minima — even when a lower-energy ligand pose is close and obvious.

The developers of [Smina](https://github.com/blang/smina), a fork of Vina with several improvements, recognized this issue and enhanced the **step-size calculation** used in Vina’s BFGS implementation. Their optimization significantly improves local search performance.

Unfortunately, Smina does **not support Vina’s `--maps` input**, which is a critical feature for our use case. Therefore, this fork was created by **porting the improved BFGS step-size logic from Smina into Vina**, enabling better local optimization while retaining support for `--maps`.

## Features

- The usage is **identical to Vina**.
- During local minimization, the **optimized BFGS step-size calculation method** from Smina is **automatically invoked**. This helps the ligand to better find local minima during the docking process.

## Installation & Usage

- Follow the standard compilation instructions for AutoDock Vina. The usage is **exactly the same as Vina**. 

## References

- AutoDock Vina: https://github.com/ccsb-scripps/AutoDock-Vina
- Smina: https://github.com/blang/smina
