# TLS-Handshake-Process-TLS-1.2-.
## 🔁 TLS 1.2 Handshake Flow Diagram

Client 🖥️                                  Server 🌐
--------------------------------------------------------
ClientHello  ───────────────▶
(TLS version, cipher suites,
 client random)

                        ◀───────────────  ServerHello
                                           (Chosen TLS version,
                                            cipher suite,
                                            server random)

                        ◀───────────────  Certificate 📜
                                           (Server public key)

                        ◀───────────────  ServerKeyExchange*
                                           (ECDHE parameters)

                        ◀───────────────  ServerHelloDone

ClientKeyExchange ───────▶
(Encrypted Pre-Master Secret
 or ECDHE public key)

ChangeCipherSpec ───────▶
Finished 🔒              ───────▶

                        ◀───────────────  ChangeCipherSpec
                        ◀───────────────  Finished 🔒

🔐 Secure Encrypted Communication Begins

🔐 Step-by-Step: How Encryption Keys Are Agreed Securely (TLS 1.2)
1️⃣ ClientHello 📤

Client sends:

Supported TLS versions

Supported cipher suites

Client Random

No encryption yet

2️⃣ ServerHello 📥

Server selects:

TLS version (e.g., TLS 1.2)

Cipher suite (e.g., ECDHE_RSA + AES)

Sends Server Random

3️⃣ Server Authentication 📜

Server sends its digital certificate

Certificate contains:

Server public key

CA signature

🔍 Client verifies:

CA trust

Domain name

Certificate validity

4️⃣ Key Exchange 🔑

Two common methods:

🔹 RSA Key Exchange (Older)

Client generates Pre-Master Secret

Encrypts it using server’s public key

Sends it to server

🔹 ECDHE (Modern & Secure ✅)

Server sends ephemeral public key

Client generates its own ephemeral key

Both compute the same shared secret

Provides Perfect Forward Secrecy 🔁

5️⃣ Session Key Derivation 🔐

Both client and server independently compute:

Session Keys = PRF(
  Pre-Master Secret,
  Client Random + Server Random
)

Generated keys include:

Encryption key

MAC (integrity) key

IV (Initialization Vector)

6️⃣ ChangeCipherSpec 🔄

Both sides signal:

“From now on, use encryption 🔒”

7️⃣ Finished Messages ✅

Encrypted handshake hash is exchanged

Confirms:

Keys match

Handshake integrity

8️⃣ Secure Communication Begins 🚀

All application data is encrypted using:

Symmetric encryption (AES / ChaCha20)

Provides:

🔒 Confidentiality

🛡️ Integrity

🧾 Authentication
