# TryHackMe — Inside a Computer System

## Room Information

* **Platform:** TryHackMe
* **Room:** Inside a Computer System
* **Category:** Pre Security
* **Difficulty:** Easy
* **Estimated Time:** 45 minutes
* **Status:** Completed — 100%

---

## 1. Introduction

The **Inside a Computer System** room explains the fundamental components of a computer and what happens internally when a computer starts.

This room provides a basic understanding of how hardware, firmware, memory, storage, and the operating system work together during the boot process.

---

## 2. Learning Objectives

By completing this room, I learned:

* Basic components inside a computer system
* The purpose of the CPU, RAM, storage, and motherboard
* The role of firmware
* The difference between BIOS and UEFI
* What happens during POST
* How a computer selects a boot device
* The role of the bootloader
* How the operating system is loaded into RAM
* The basic sequence of the computer boot process

---

# Task 1 — Introduction

The first task introduces the concept of a computer system and explains that a computer consists of multiple hardware and software components working together.

A computer requires hardware components such as:

* CPU
* RAM
* Storage
* Motherboard
* Power Supply
* Input and Output devices

These components work together to execute instructions and run the operating system and applications.

---

# Task 2 — Inside a Computer System

## CPU

The **Central Processing Unit (CPU)** is responsible for executing instructions and performing calculations.

It processes instructions provided by programs and coordinates operations performed by other components.

---

## RAM

**Random Access Memory (RAM)** is temporary memory used by the computer to store data and instructions that are currently being used.

RAM is volatile, meaning its contents are lost when the computer is powered off.

---

## Storage

Storage devices such as SSDs and HDDs are used to permanently store:

* Operating systems
* Applications
* Documents
* Configuration files
* Other user data

Unlike RAM, storage retains data after the computer is powered off.

---

## Motherboard

The motherboard connects the major components of the computer together.

It allows components such as the CPU, RAM, storage, and other hardware devices to communicate with each other.

---

## Power Supply

The **Power Supply Unit (PSU)** provides electrical power to the computer's components.

When the power button is pressed, the PSU receives a signal and begins supplying power to the system.

---

# Task 3 — What Happens When You Press the Start Button?

When the computer's power button is pressed, several stages occur before the operating system becomes available.

The basic boot sequence is:

```text
Power Button
     ↓
Power Supply
     ↓
UEFI / Firmware
     ↓
POST
     ↓
Boot Device Selection
     ↓
Bootloader
     ↓
Operating System
     ↓
Computer Ready
```

---

## Step 1 — Pressing the Power Button

When the power button is pressed, the computer sends a signal to the **Power Supply Unit (PSU)**.

The PSU then provides power to the required hardware components.

---

## Step 2 — Firmware Starts

After power is supplied, the computer's firmware starts.

Modern computers generally use **UEFI (Unified Extensible Firmware Interface)**.

Older systems commonly used **BIOS (Basic Input/Output System)**.

UEFI has largely replaced traditional BIOS on modern computers.

The firmware performs important initialization tasks and prepares the system for booting.

---

## Step 3 — POST

The firmware performs a **Power-On Self Test (POST)**.

POST checks whether the required hardware components are:

* Present
* Properly configured
* Functioning correctly

This helps ensure that the computer has the necessary hardware available before attempting to load the operating system.

---

## Step 4 — Selecting the Boot Device

After POST, the firmware determines which device should be used to boot the operating system.

UEFI uses a configured **boot priority/order**.

Possible boot devices include:

* SSD
* HDD
* USB drive
* Network boot device

The firmware selects a suitable boot device according to the configured boot order.

---

## Step 5 — Initiating the Bootloader

Once the boot device has been selected, the firmware starts the **bootloader**.

The bootloader is responsible for beginning the process of loading the operating system.

The operating system is transferred from the boot device into **RAM**.

After the operating system is ready to take control, UEFI transfers control from the firmware to the operating system.

---

## Complete Boot Process

```text
┌──────────────────────┐
│     Power Button     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│     Power Supply     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│    UEFI / Firmware   │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│        POST          │
│ Hardware Verification│
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│    Boot Device       │
│      Selection       │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│     Bootloader       │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Operating System   │
│      → RAM           │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   System Ready       │
└──────────────────────┘
```

---

# Task 4 — Conclusion

The room provided an understanding of what happens inside a computer from the moment the power button is pressed until the operating system starts.

The boot process can be summarized as:

1. The power button is pressed.
2. The PSU supplies power.
3. UEFI firmware starts.
4. POST checks the hardware.
5. The firmware selects a boot device.
6. The bootloader starts.
7. The operating system is loaded into RAM.
8. Control is transferred to the operating system.

---

# Practical Exercise

I completed the practical exercise provided in the room and successfully completed the required task.

**Status:** Completed successfully

---

# Key Concepts Learned

| Concept     | Description                                                    |
| ----------- | -------------------------------------------------------------- |
| CPU         | Executes instructions and performs calculations                |
| RAM         | Temporary memory used by running processes                     |
| Storage     | Permanently stores data and operating systems                  |
| Motherboard | Connects and enables communication between hardware components |
| PSU         | Supplies electrical power to the system                        |
| UEFI        | Modern firmware interface used during system startup           |
| BIOS        | Older firmware standard largely replaced by UEFI               |
| POST        | Checks hardware during startup                                 |
| Boot Device | Device containing the operating system or bootable data        |
| Bootloader  | Starts the operating system loading process                    |

---

# Cybersecurity Relevance

Understanding the computer boot process is important for cybersecurity because security professionals need to understand how a system operates from the hardware and firmware level upward.

Knowledge of UEFI, bootloaders, RAM, storage, and operating system initialization provides a foundation for understanding areas such as:

* Secure Boot
* Boot-level attacks
* Firmware security
* Rootkits
* Persistence mechanisms
* Operating system security
* Endpoint security
* Digital forensics

---

# What I Learned

Through this room, I developed a basic understanding of how a computer starts and how different hardware and software components interact during the boot process.

The most important concept I learned was that starting a computer is a sequence of stages rather than a single operation:

**Power → Firmware → POST → Boot Device → Bootloader → Operating System**

This knowledge provides a foundation for further learning in computer architecture, operating systems, cybersecurity, and digital forensics.

---

# Skills Demonstrated

* Computer Fundamentals
* Hardware Fundamentals
* Operating System Fundamentals
* UEFI / BIOS Fundamentals
* Boot Process
* Basic Cybersecurity Concepts
* TryHackMe Practical Learning

---

# Completion

**TryHackMe Room:** Inside a Computer System

**Completion Status:** 100% Completed

**Difficulty:** Easy

**Category:** Pre Security

**Primary Topic:** Computer Fundamentals and Boot Process


## 👨‍💻 Author

**Balamurugan P**

Cybersecurity Analyst | Network Security | Threat Detection

