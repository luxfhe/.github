# Lux FHE 🔐

**Fully Homomorphic Encryption for Everyone**

Lux FHE is an open-source ecosystem for building privacy-preserving applications using Fully Homomorphic Encryption (FHE). Compute on encrypted data without ever decrypting it.

## 🎯 What is FHE?

Fully Homomorphic Encryption allows computations on encrypted data:
- **Private ML**: Train and run models on encrypted data
- **Private Analytics**: Process sensitive data without exposure
- **Confidential Computing**: Execute business logic on encrypted inputs
- **Private Smart Contracts**: Blockchain with encrypted state

## 📦 Core Libraries

| Repository | Description | Language |
|------------|-------------|----------|
| [luxfi/fhe](https://github.com/luxfi/fhe) | Core FHE library | Go |
| [luxfi/lattice](https://github.com/luxfi/lattice) | Lattice cryptography | Go |
| [luxfi/torus](https://github.com/luxfi/torus) | FHE compiler & runtime (Python, C++) | Python/C++ |
| [luxfi/torus-ml](https://github.com/luxfi/torus-ml) | Machine Learning on encrypted data | Python |
| [luxfi/torus-ntt](https://github.com/luxfi/torus-ntt) | NTT acceleration | Rust |
| [luxfi/torus-fft](https://github.com/luxfi/torus-fft) | FFT acceleration | Rust |
| [luxfi/fhe-compiler](https://github.com/luxfi/fhe-compiler) | LLVM-based FHE compiler | C++ |

## 🌍 Language Bindings

FHE for every language via LLVM-based compilation:

| Language | Package | Status |
|----------|---------|--------|
| Python | `pip install luxfhe` | ✅ Full |
| Go | `github.com/luxfi/fhe` | ✅ Full |
| Rust | `luxfhe` crate | ✅ Full |
| C/C++ | `libluxfhe` | ✅ Full |
| Node.js | `@luxfhe/core` | ✅ Full |
| Ruby | `luxfhe` gem | 🚧 Beta |
| Elixir | `luxfhe` hex | 🚧 Beta |
| Haskell | `luxfhe` hackage | 🚧 Beta |

## 📚 Documentation & Learning

| Resource | Description |
|----------|-------------|
| [docs](https://github.com/luxfhe/docs) | Full documentation site |
| [examples](https://github.com/luxfhe/examples) | Multi-language examples |
| [handbook](https://github.com/luxfhe/handbook) | Deep dive into FHE concepts |
| [workshop](https://github.com/luxfhe/workshop) | Interactive tutorials |

## 🚀 Quick Start

### Python
```python
from luxfhe import Client, Server

# Client encrypts
client = Client()
a = client.encrypt(42)
b = client.encrypt(8)

# Server computes on encrypted data
server = Server()
result = server.add(a, b)  # Still encrypted!

# Client decrypts
print(client.decrypt(result))  # 50
```

### Go
```go
import "github.com/luxfi/fhe"

client := fhe.NewClient()
a := client.Encrypt(42)
b := client.Encrypt(8)

server := fhe.NewServer()
result := server.Add(a, b)

fmt.Println(client.Decrypt(result)) // 50
```

### Rust
```rust
use luxfhe::{Client, Server};

let client = Client::new();
let a = client.encrypt(42u64);
let b = client.encrypt(8u64);

let server = Server::new();
let result = server.add(&a, &b);

println!("{}", client.decrypt(&result)); // 50
```

## 🔗 Use Cases

### Private Machine Learning
```python
from luxfhe.ml import EncryptedModel

# Train on encrypted data
model = EncryptedModel.load("classifier.fhe")
encrypted_input = client.encrypt(user_data)
prediction = model.predict(encrypted_input)  # Encrypted prediction
```

### Private Agents
```python
from luxfhe.agents import PrivateAgent

# Agent operates on encrypted context
agent = PrivateAgent(model="gpt-4-fhe")
encrypted_context = client.encrypt(sensitive_data)
response = agent.run(encrypted_context)
```

### Private Smart Contracts
```solidity
// Lux FHE-enabled Solidity
import "@luxfhe/contracts/FHE.sol";

contract PrivateVault {
    euint64 private balance;
    
    function deposit(einput encryptedAmount) external {
        balance = FHE.add(balance, encryptedAmount);
    }
}
```

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    Lux FHE Ecosystem                            │
├─────────────────────────────────────────────────────────────────┤
│  Applications                                                   │
│  ┌──────────┬─────────────┬───────────────┬──────────────┐      │
│  │ Private  │   Private   │    Private    │   Private    │      │
│  │   ML     │   Agents    │   Analytics   │   Contracts  │      │
│  └────┬─────┴──────┬──────┴───────┬───────┴───────┬──────┘      │
│       │            │              │               │             │
│  ┌────▼────────────▼──────────────▼───────────────▼──────┐      │
│  │              Lux FHE Runtime (torus)                  │      │
│  └────┬──────────────────────────────────────────────────┘      │
│       │                                                         │
│  ┌────▼────────────────────────────────────────────────────┐    │
│  │            LLVM-based FHE Compiler                      │    │
│  │  ┌─────────┬─────────┬─────────┬─────────┬─────────┐    │    │
│  │  │ Python  │   Go    │  Rust   │  C/C++  │ Node.js │    │    │
│  │  └─────────┴─────────┴─────────┴─────────┴─────────┘    │    │
│  └────┬────────────────────────────────────────────────────┘    │
│       │                                                         │
│  ┌────▼────────────────────────────────────────────────────┐    │
│  │          Core Cryptography (luxfi/fhe + lattice)        │    │
│  │  ┌─────────────┬─────────────┬─────────────────────┐    │    │
│  │  │  TFHE/CKKS  │  NTT/FFT    │  GPU Acceleration   │    │    │
│  │  └─────────────┴─────────────┴─────────────────────┘    │    │
│  └─────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────┘
```

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](https://github.com/luxfhe/docs/blob/main/CONTRIBUTING.md).

## 📄 License

Apache 2.0 - See individual repositories for details.

---

**Built by [Lux Network](https://lux.network) & [Hanzo AI](https://hanzo.ai)**
