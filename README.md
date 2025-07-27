# 🧪 TESTNET TASK 3: OCS01 Smart Contract Testing CLI

> ⚠️‼️ PREVIOUSLY TESTNET TASK 2: [Octra Private Transfer Features](https://github.com/izmerGhub/TESTNET-2-Octra-Testnet-Encrypt-and-Decrypt-Features--Izmer?tab=readme-ov-file#-previously-octra-testnet-task-1-wallet-and-token-setup) ⚠️‼️

This guide walks you through interacting with the **OCS01 smart contract** using the official `ocs01-test` Rust-based CLI client. You will test all contract methods through an interactive terminal UI.

---

## 🔧 What is OCS01-Test CLI?

A smart contract tester built in Rust to:

- 🧪 Test all contract methods.
- 🎛️ Provide interactive menu navigation.
- ⚡ Instantly show output for view methods.
- 🔏 Handle signing for call methods.

Compatible with:

- ✅ Linux
- ✅ macOS

---

## ⚙️ Step A: Install Dependencies (Linux & macOS)

### 🐧 Linux

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential curl git nano lz4 jq tmux
```

### 🍎 macOS

```bash
xcode-select --install     # For essential developer tools
brew update
brew install git curl jq nano lz4 pkg-config
```

### 🦀 Step B: Install Rust (if not already)

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```

### 🏗️ Step C: Clone & Build the CLI

```bash
git clone https://github.com/octra-labs/ocs01-test.git
cd ocs01-test
cargo build --release
```

🛠️ The binary will be located at:

```bash
./target/release/ocs01-test
```

### 📂 Step D: Prepare Required Files

#### 🔁 Copy the Contract Interface

```bash
cp EI/exec_interface.json .
```

This file contains ABI for the contract at:

```
octBUHw585BrAMPMLQvGuWx4vqEsybYH9N7a3WNj1WBwrDn
```

⚠️ Do not modify this file!

#### 📝 Create wallet.json

```bash
nano wallet.json
```

Paste this and edit your credentials:

```json
{
  "private_key": "your-private-key-here",
  "address": "your-octra-address-here", 
  "rpc_endpoint": "https://octra.network"
}
```

✅ Replace:

- `"private-key-here"` → Your Base64-encoded private key  
- `"octxxxxxxxxxx..."` → Your Octra testnet address

💾 Save and exit.

### 🚀 Step E: Run the Test CLI

```bash
./target/release/ocs01-test
```

You will see:

```text
--- ocs01 test client ---
contract: octBUHw585BrAMPMLQvGuWx4vqEsybYH9N7a3WNj1WBwrDn
your balance: 115.218314 oct (nonce: 23)

select method:
1. greeting (get personal msg)
2. contract info (get contract description)
3. claim 1 token (only once per address)
4. check token balance
5. dot product (x1 * x2 + y1 * y2)
6. vector magnitude sqrt(x^2 + y^2)
7. power (base^exponent)
8. factorial (n!)
9. fibonacci number
10. greatest common divisor
11. check if number is prime
12. 2x2 matrix determinant (ad - bc)
13. linear interpolation
14. modular exponentiation (base^exp mod m)
0. exit
```

### 🔢 Step F: Test Math Functions 1-by-1

Use the number menu to test each feature:

| Method | Description            | Notes                                   |
|--------|------------------------|-----------------------------------------|
| 1️⃣     | greeting               | Returns a custom message.                |
| 2️⃣     | contract info          | Shows smart contract description.       |
| 3️⃣     | claim 1 token          | Only once per address — claim test token.|
| 4️⃣     | check token balance    | Displays your OCT balance.               |
| 5️⃣     | dot product            | Input: x1, x2, y1, y2 → Output: x1x2 + y1y2 |
| 6️⃣     | vector magnitude       | Input: x, y → Output: √(x² + y²)        |
| 7️⃣     | power                  | Input: base, exponent → Output: base^exponent |
| 8️⃣     | factorial              | Input: n → Output: n!                    |
| 9️⃣     | fibonacci              | Input: n → Output: nth Fibonacci number |
| 🔟     | GCD                    | Input: a, b → Output: greatest common divisor |
| 1️⃣1️⃣  | is prime               | Input: n → Output: true/false            |
| 1️⃣2️⃣  | 2x2 determinant        | Input: a, b, c, d → Output: ad - bc     |
| 1️⃣3️⃣  | linear interpolation   | Input: x0, y0, x1, y1, x → Output: interpolated y |
| 1️⃣4️⃣  | modular exponentiation | Input: base, exp, mod → Output: (base^exp) % mod |

✅ Test all 14 options to complete the task. Record outputs or screenshots if needed.

```
choice: 1️⃣

--- greetCaller ---

result: "Greetings, oct5VXSG3UmtQwgvVzhs6ojpwmvoFmDihyRoDrXLcR4h4bY! Welcome to OCS01."

press enter to continue...

--- ocs01 test client ---
contract: octBUHw585BrAMPMLQvGuWx4vqEsybYH9N7a3WNj1WBwrDn
your balance: 116.218314 oct (nonce: 22)

select method:
...
```
```
choice: 2️⃣

--- getSpec ---

result: "OCS01: math & test token distribution contract (v.0.0.12)"

press enter to continue...

...

choice: 3️⃣

--- claimToken ---

tx: 038e3fb086a928de14b29b55771072163ea094f4cb8d34cdf0dca66e9f06c76e
wait for confirmation? y/n: y
waiting....
error: api error:

press enter to continue...

...
```
```
choice: 3️⃣

--- claimToken ---

tx: d844541396fed899d2022b0c75e1aa652f48b2876f229f4ed12f2cad380263e5
wait for confirmation? y/n: y
waiting........
confirmed

press enter to continue...

...
```
```
choice: 4️⃣

--- getCredits ---
address (e.g. octXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX): oct5VXSG3UmtQwgvVzhs6ojpwmvoFmDihyRoDrXLcR4h4bY

result: "1000000000000"

press enter to continue...

...
```
```
choice: 5️⃣

--- dotProduct ---
x1: 1
y1: 2
x2: 3
y2: 4

result: "11"

press enter to continue...

...
```
```
choice: 6️⃣

--- vectorMagnitude ---
x: 1
y: 2

result: "2"

press enter to continue...

...
```
```
choice: 7️⃣

--- power ---
base: 1
exponent (max: 255): 5

result: "1"

press enter to continue...

...
```
```
choice: 8️⃣

--- factorial ---
n (max: 20): 5

result: "120"

press enter to continue...

...
```
```
choice: 9️⃣

--- fibonacci ---
n (max: 100): 54

result: "86267571272"

press enter to continue...

...
```
```
choice: 🔟

--- gcd ---
a: 4
b: 3

result: "1"

press enter to continue...

...
```
```
choice: 1️⃣1️⃣

--- isPrime ---
n: 1

result: "0"

press enter to continue...

...
```
```
choice: 1️⃣2️⃣

--- matrixDeterminant2x2 ---
a: 22
b: 32
c: 1
d: 3

result: "34"

press enter to continue...

...
```
```
choice: 1️⃣3️⃣

--- linearInterpolate ---
x0: 1
y0: 5
x1: 3
y1: 6
x: 2

result: "5"

press enter to continue...

...
```
```
choice: 1️⃣4️⃣

--- modularExponentiation ---
base: 2
exp: 5
mod: 2

result: "0"

press enter to continue...
```
