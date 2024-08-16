Port Scanner with Multi-threading
This Rust program is a simple TCP port scanner that uses multi-threading to scan a range of ports on a given IP address. Below is a detailed explanation of how the program works, from running the command to its completion.

How to Run
To execute the program, use the following command:

```
cargo run -- -j 10 172.19.101.157
```
How It Works
Command Execution:

Running `cargo run -- -j 10 172.19.101.157` builds the Rust project and executes the binary.
The -- separates cargo run arguments from those intended for the binary itself, passing -j 10 172.19.101.157 to the Rust program.
Argument Parsing:

The program starts by collecting command-line arguments into a vector: args.
These arguments are then parsed to extract the number of threads (-j 10) and the IP address (172.19.101.157).
Inside Arguments::new:

The program checks the number of arguments to ensure they are valid.
It parses the number of threads (10) and the IP address (172.19.101.157).
An Arguments struct is created, storing the flag, IP address, and number of threads.
Spawning Threads:

The main function retrieves the number of threads and IP address from the Arguments struct.
It creates a channel for inter-thread communication and spawns multiple threads.
Each thread scans a specific range of ports based on its thread ID.
Port Scanning:

Threads attempt to establish a TCP connection on each port within their assigned range.
If a connection is successful, the port number is sent back to the main thread via the channel.
The scanning loop continues until all relevant ports are checked.
Collecting Results:

The main thread collects open ports reported by the scanning threads.
It sorts the list of open ports and prints them to the console.
Program Termination:

After all ports are scanned, and the results are printed, the program exits.
Example Output
When you run the program, the output will indicate which ports are open on the specified IP address:

```
.
.
.
80 is open
443 is open
```

The program scans ports from 1 to 65535 on the specified IP address.
Multi-threading allows for faster scanning by dividing the workload across multiple threads.
Adjust the number of threads using the -j flag for different performance requirements.
