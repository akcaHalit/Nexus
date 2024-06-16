# Nexus

> I deployed a contract for Nexus and backed up my files.
> 
<details>
  <summary> <h1> About the Investment  </summary> </h1>
    
![image][339684455-9fcbe5d7-d88c-49b8-af65-768132f75176](https://github.com/akcaHalit/Nexus/assets/103420587/1f3532ac-a110-4b87-84c8-76c7c8bafc0b)

</details>

# Installation

```console
# update
sudo apt update -y && sudo apt upgrade -y
sudo apt install cmake
sudo apt install build-essential
```

#

```console
# installing rustup

# choose option 1
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# after rust installation
. "$HOME/.cargo/env"
rustup target add riscv32i-unknown-none-elf
```

#

```console
# installing nexus tool

# this may take a while - no worries if you see errors.
cargo install --git https://github.com/nexus-xyz/nexus-zkvm nexus-tools --tag 'v1.0.0'

# creating nexus project
cargo nexus new nexus-project

# we'll change main.rs
cd nexus-project
```

#

```console

# open this file
nano ./src/main.rs
# delete the existing code and enter the following block
```

```console
#![no_std]
#![no_main]

fn fib(n: u32) -> u32 {
    match n {
        0 => 0,
        1 => 1,
        _ => fib(n - 1) + fib(n - 2),
    }
}

#[nexus_rt::main]
fn main() {
    let n = 7;
    let result = fib(n);
    assert_eq!(result, 13);
}
```

#

```console
# let's run the contract
cargo nexus run
cargo nexus run -v

# wait for the processes to prove
cargo nexus prove

# complete the verification process
cargo nexus verify
```

#
 
> Save and store the `nexus-proof` file in this directory.
<img width="417" alt="Ekran Resmi 2024-06-14 11 02 40" src="https://github.com/ruesandora/Nexus/assets/101149671/b6468869-3274-4b05-857d-a82263729585">

> That's all the processes.
> Thanks to [Rues](https://github.com/ruesandora)

