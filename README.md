![Java](https://img.shields.io/badge/Made%20with-Java-orange?style=flat-square&logo=java)

<h1 align="center">🔐 MultiChat Crypted (Local)</h1>

<p align="center">
  <strong>A secure, multi-threaded Java Chat Application with a clean Visual Interface.</strong>
</p>

<div align="center">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white" alt="Java" />
  <img src="https://img.shields.io/badge/Security-Encryption-red?style=for-the-badge" alt="Security" />
  <img src="https://img.shields.io/badge/UI-Swing/AWT-blue?style=for-the-badge" alt="UI" />
</div>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- TABLE OF CONTENTS -->
<h2 id="table-of-contents"> :book: Table of Contents </h2>

<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about"> ➤ About The Project</a></li>
    <li><a href="#key-features"> ➤ Key Features</a></li>
    <li><a href="#install"> ➤ Getting Started</a></li>
    <li><a href="#usage"> ➤ How to Use & Commands</a></li>
    <li><a href="#architecture"> ➤ Technical Architecture</a></li>
    <li><a href="#acknowledgements"> ➤ Credits & Acknowledgements</a></li>
  </ol>
</details>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2 id="about"> :cloud: About The Project</h2>

MultiChat Crypted is a robust Java-based messaging system designed to explore **thread management** and **synchronous/asynchronous communication**. It features a server-client architecture where multiple users can communicate in real-time within a secure local environment.

> [!IMPORTANT]
> This project focuses on the practical implementation of network sockets and basic cryptographic principles in a GUI environment.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2 id="key-features"> :star2: Key Features</h2>

- 🧵 **Multi-threaded Server**: Handles dozens of simultaneous connections without hanging.
- 🔒 **Encrypted Pipeline**: Basic security layer to protect message integrity.
- 🎨 **Visual Interface**: User-friendly GUI for messaging (no terminal commands needed for chatting).
- ✉️ **Private Messaging**: Direct communication link between specific users using `/mp`.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2 id="install"> 🚀 Getting Started</h2>

To launch the MultiChat application in your local environment, follow these steps:

1.  **Start the Server**: Run the `ChatServer.java` class first to listen for connections.
2.  **Launch Clients**: Start multiple instances of `ChatGUI.java`. Each instance represents a unique user in the chat room.

> [!TIP]
> Make sure your firewall allows local socket connections on the port specified in the source code.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2 id="usage"> 📜 Commands & Usage</h2>

Interact with the chat using these built-in commands:

| Command | Description |
| :--- | :--- |
| `/nick <name>` | Change your current nickname to a new one. |
| `/mp <name> <message>` | Send a private, encrypted message to a specific user. |
| `/bye` | Safely disconnect and close the application. |

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2 id="architecture"> ⚙️ Architecture Details</h2>

The application follows a Robust Client-Server model with specific security handshake phases:

### 🛡️ Security Handshake Phase
1.  **Public Key Exchange**: Upon connection, the Client generates an **RSA KeyPair** and sends the **Public Key** to the Server.
2.  **Session Key Generation**: The Server generates a unique **AES Session Key**.
3.  **Encrypted Key Delivery**: The Server encrypts the AES key using the Client's RSA Public Key and sends it back.
4.  **Secure Tunnel**: All subsequent messages are encrypted/decrypted using that shared AES key.

### 🏗️ Server Side (`Server.java`)
*   **ConnectionHandler**: An inner class implementing `Runnable`, dedicated to managing each client's input/output streams.
*   **Broadcast Engine**: Logic to distribute messages to all connected users or target specific users for private messages (`/mp`).
*   **Concurrency**: Uses `Executors.newCachedThreadPool()` to handle scaling client numbers efficiently.

### 🎨 Client Side (`Client.java` & `ChatGUI.java`)
*   **Dual-Threaded Client**: One thread manages the **InputHandler** (outgoing messages) while the primary thread listens for incoming encrypted data from the server.
*   **UI Synchronization**: Uses `SwingUtilities.invokeLater` to ensure the AWT/Swing interface updates safely across threads.
*   **Protocol Handler**: Translates raw encrypted byte arrays from the socket back into readable strings.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2 id="acknowledgements"> 🤝 Acknowledgements</h2>

This project was a joint effort where both developers contributed to all aspects of the application, including the core logic, security, and the AWT interface:

*   **<a href="https://github.com/L0rest">L0rest</a>** 
*   **<a href="https://github.com/SteelPotathor">SteelPotathor</a>** 

---
<p align="center">
  <i>Educational Project - Designed for Local Environment Testing.</i>
</p>
