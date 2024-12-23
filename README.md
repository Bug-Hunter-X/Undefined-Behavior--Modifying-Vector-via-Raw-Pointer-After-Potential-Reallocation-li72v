# Rust Bug: Undefined Behavior with Raw Pointers and Vectors

This repository demonstrates a common error in Rust: modifying a vector's contents using a raw pointer after the vector might have been reallocated.  This results in undefined behavior, as the raw pointer may no longer point to a valid memory location within the vector. 

The `bug.rs` file shows the erroneous code. The `bugSolution.rs` provides a corrected version illustrating safe vector manipulation.

**How to Reproduce:**
1. Clone this repository.
2. Navigate to the project directory.
3. Compile and run `bug.rs` using `cargo run`. Observe the potentially unexpected or erratic behavior.
4. Compile and run `bugSolution.rs` to see the correct and safe approach.

**Cause:**  Direct pointer manipulation bypasses Rust's memory safety guarantees. Vectors can reallocate their internal storage when their capacity is exceeded, rendering any previously obtained raw pointer invalid.

**Solution:** Avoid using raw pointers with vectors unless absolutely necessary and with extreme caution. Employ safe methods provided by the Rust standard library for accessing and manipulating vector elements.