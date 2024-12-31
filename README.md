# Unintended Latch in VHDL Process

This repository demonstrates a common error in VHDL: an unintended latch created when a signal is not assigned a value in all possible process branches.  This example shows the problem and its solution.

**Problem:** The original `my_entity` has a process that updates `internal_data` only when `reset` is '1' or when a rising clock edge occurs and `data_in` is available. It's missing an assignment for the `else` condition, unintentionally creating a latch which holds the previous value of `internal_data` when neither condition is met, likely leading to unexpected behaviour.

**Solution:** The solution adds an `else` clause in the process to handle the situation where neither the reset nor the rising clock edge conditions are met.  This ensures that `internal_data` has a defined value in all cases, eliminating the unintended latch.  

Proper handling of signal assignments is crucial to avoid such errors in VHDL. This prevents glitches and other timing issues in hardware implementation.