Here's a clean and informative `README.md` file tailored for your Assembly-based **PingPong Game** project. It includes an overview, how BIOS interrupts work, a brief explanation of how assembly works in this context, and how to run the program.

---

````markdown
# 🕹️ PingPong Game (x86 Assembly)

A fun hobby project built using x86 Assembly language, simulating a simple PingPong game in **Mode 13h** (320x200 256-color graphics mode). This project is a demonstration of low-level graphics programming, direct memory access, and BIOS interrupts in MS-DOS or emulated DOS environments.

---

## 📌 Features

- Two-player paddle control:
  - Player 1: `W` and `S` keys
  - Player 2: `O` and `L` keys
- Ball bouncing with collision detection
- Visual rendering using Mode 13h graphics
- Real-time keyboard input
- Frame-buffer manipulation via video memory

---

## 🛠️ How It Works

### 🔧 Assembly Language

Assembly is a low-level programming language that gives direct control over hardware using mnemonic codes for processor instructions. In this project, we use **16-bit x86 Assembly** targeted at DOS environments.

Key characteristics:

- Direct video memory manipulation: writing to segment `0xA000` to draw pixels
- Port I/O for keyboard input handling
- Jump and loop instructions for game logic
- Optimized for minimal instruction cycles

---

### 🧠 BIOS Interrupts Used

BIOS interrupts provide access to basic hardware services via the **INT instruction**. These are essential in real-mode DOS programs.

| Interrupt | Purpose | Description |
|----------|---------|-------------|
| `INT 10h` | Video Services | Used to set video mode and draw pixels |
| `INT 16h` | Keyboard Services | Detects and reads keyboard input |
| `INT 21h` | DOS Services | Used to exit program or other DOS-level operations |

#### Examples:

- **Set Video Mode (Mode 13h):**
  ```asm
  mov ah, 0       ; Function: Set video mode
  mov al, 13h     ; 320x200, 256 colors
  int 10h
````

* **Read Keyboard Input (Blocking):**

  ```asm
  mov ah, 00h     ; Wait for key press
  int 16h         ; Returns ASCII in AL, scan code in AH
  ```

* **Exit to DOS:**

  ```asm
  mov ax, 4C00h   ; Terminate program
  int 21h
  ```

---

## 🎮 Controls

| Player       | Key Up | Key Down |
| ------------ | ------ | -------- |
| Left Paddle  | `W`    | `S`      |
| Right Paddle | `O`    | `L`      |

---

## ▶️ Running the Game

### Requirements

* DOS emulator (e.g., [DOSBox](https://www.dosbox.com/))
* TASM or MASM assembler (for compilation)
* 16-bit real-mode compatible environment

### Steps

1. Run the game in DOSBox:

   ```bash
   masm /a pong.asm
   link pong
   dosbox pong.exe
   ```

---

## 📚 Learning Resources

* [PC BIOS Interrupts List (Ralf Brown's)](http://www.ctyme.com/intr/int.htm)
* [x86 Assembly Guide (University of Virginia)](https://www.cs.virginia.edu/~evans/cs216/guides/x86.html)
* [DOSBox Manual](https://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox)

---

## 🧑‍💻 Author

Made with 💾 and a love for retro computing.
Feel free to fork, tinker, and have fun!
