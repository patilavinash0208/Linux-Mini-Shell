# 🐚 Linux Mini Shell

A custom command-line interpreter written in **C** that emulates the core functionality of a Linux shell — built-in commands, external command execution, pipelines, job control, and Unix signal handling, all powered by low-level Linux system calls.

![Language](https://img.shields.io/badge/Language-C-blue.svg)
![Platform](https://img.shields.io/badge/Platform-Linux-informational.svg)
![Build](https://img.shields.io/badge/Build-Makefile-success.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 📖 Overview

**Linux Mini Shell** is a lightweight Unix shell implementation that demonstrates practical, hands-on knowledge of Linux system programming. It provides a customizable prompt, executes both built-in and external commands, supports multi-stage pipelines, and manages foreground/background jobs — all while gracefully handling signals like `SIGINT`, `SIGTSTP`, and `SIGCHLD`.

This project is a deep dive into how real shells (like `bash` or `zsh`) work under the hood, using core system calls such as `fork()`, `execvp()`, `pipe()`, and `waitpid()`.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🖥️ Custom Prompt | Configurable `PS1`-style shell prompt |
| ⚙️ Built-in Commands | Native implementations of common shell commands |
| 🚀 External Commands | Runs any Linux binary via `execvp()` |
| 🔗 Pipelines | Chain multiple commands together with `\|` |
| 🎛️ Job Control | Foreground & background process execution |
| 🛑 Signal Handling | Custom handling for `SIGINT`, `SIGTSTP`, `SIGCHLD` |
| 🧩 Process Management | Clean process creation, tracking, and cleanup |
| 📝 Command Parsing | Robust input tokenization and parsing |
| 📂 Directory Awareness | Displays and tracks current working directory |
| 🌱 Environment Variables | Support for shell environment variables |

---

## 🧰 Built-in Commands

| Command | Description |
|---|---|
| `cd` | Change the current working directory |
| `pwd` | Print the current working directory |
| `exit` | Exit the shell |
| `echo $$` | Print the current shell's PID |
| `echo $?` | Print the exit status of the last command |
| `echo $SHELL` | Print the current shell path |
| `jobs` | List background/stopped jobs |
| `fg` | Bring a background job to the foreground |
| `bg` | Resume a stopped job in the background |

---

## 💻 External Commands

Mini Shell executes any standard Linux command using `execvp()`:

```bash
ls
cat file.txt
grep main *.c
mkdir test
rm file.txt
```

---

## 🔗 Pipe Support

Supports chaining multiple commands together through pipes, just like a real shell:

```bash
cat file.txt | grep main | wc
```

---

## 🚦 Signal Handling

Mini Shell implements custom signal handlers to keep the shell alive and in control:

- **🔸 `SIGINT` (Ctrl + C)**
  - Prevents termination of the shell itself.
  - Terminates only the active foreground process.

- **🔸 `SIGTSTP` (Ctrl + Z)**
  - Stops the current foreground process.
  - Stores it as a stopped job for later resumption.

- **🔸 `SIGCHLD`**
  - Automatically cleans up terminated child processes to avoid zombies.

---

## 🗂️ Job Control

Basic job management is supported via:

```bash
jobs   # List all background/stopped jobs
fg     # Resume a job in the foreground
bg     # Resume a stopped job in the background
```

---

## 🛠️ Technologies Used

- 🔤 Advanced C
- 🐧 Linux System Programming
- 🧵 Process Management
- 📡 Signals
- 🔗 Pipes
- 🍴 `fork()`
- ▶️ `execvp()`
- ⏳ `waitpid()`
- 🔀 `dup2()`
- 📁 File Handling
- 🧱 Makefiles

---

## 📁 Project Structure

```text
.
├── main.c                  # Entry point of the shell
├── scan_input.c            # Input reading and tokenizing logic
├── commands.c              # Built-in and external command execution
├── list.c                  # Job/process list management
├── shell.h                 # Shared headers and declarations
├── external_commands.txt   # Reference list of supported external commands
└── README.md                # Project documentation
```

---

## ⚙️ Working Principle

1. 🖨️ Display the shell prompt.
2. ⌨️ Read user input.
3. 🔍 Identify whether the command is built-in or external.
4. ⚡ Execute built-in commands directly within the shell process.
5. 🍴 Create child processes using `fork()` for external commands.
6. ▶️ Execute commands using `execvp()`.
7. 🔗 Support pipelines using `pipe()` and `dup2()`.
8. 🎛️ Handle foreground/background execution.
9. 📡 Process Unix signals for job control.

---

## 🔌 Linux System Calls Used

- `fork()`
- `execvp()`
- `waitpid()`
- `pipe()`
- `dup2()`
- `kill()`
- `signal()`
- `chdir()`
- `getcwd()`

---

## 🚀 Getting Started

### Prerequisites
- A Linux (or Unix-like) environment
- `gcc` and `make` installed

### Build

```bash
git clone https://github.com/patilavinash0208/mini-shell.git
cd mini-shell
make
```

### Run

```bash
./mini_shell
```

---

## 🎓 Learning Outcomes

Building Mini Shell provided hands-on experience in:

- 🧵 Linux Process Management
- 🔧 Unix System Calls
- 📡 Signal Handling
- 🔗 Inter-Process Communication (IPC)
- 🚰 Pipe Programming
- 🎛️ Job Control
- 🐚 Shell Programming
- 📝 Command Parsing
- ⏱️ Process Synchronization
- 🐧 Linux System Programming

---

## 🔮 Future Enhancements

- 📜 Command history
- ⌨️ Auto-completion
- 🔀 Input/Output redirection
- 🌱 Environment variable expansion
- 🔗 Alias support
- 🔔 Background process notifications
- 📃 Shell scripting support

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!
Feel free to check the [issues page](https://github.com/patilavinash0208/mini-shell/issues) or submit a pull request.

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 👤 Author

**Avinash Patil**

- 🐙 GitHub: [@patilavinash0208](https://github.com/patilavinash0208)
- 💼 LinkedIn: [Avinash Patil](https://www.linkedin.com/in/avinash-patil-873b9b227)

---

<p align="center">⭐ If you found this project interesting, consider giving it a star! ⭐</p>
