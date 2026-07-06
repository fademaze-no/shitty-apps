# renano - A SHSE (Shitty and Holy Strong Editor)

Have you ever been editing an important file in the terminal, only for your SSH connection to drop, crashing terminal, or your computer losing power? If that happens, your file can get corrupted, half-written or completely unusuable. 

**renano** is a script that acts like a safety shield for your files. It lets you use `nano` (the good old text editor) without risking your data getting corrupt!

---

## How it works

Instead of opening your original file directly, `renano` uses a trick called "**atomic saving**" (whatever tf that is), which is the same method that is being used by databases and banks. 



Here is how it works under the hood:
1. **The "sandbox":** Firstly, it creates a temporary copy of your file in a temporary folder (`/tmp`).
2. **Safe editing:** You open and type inside this *copy*. Your original file is not even touched yet, until you quit `nano` and have made changes.
3. **Checking the difference:** When you save and exit, `renano` uses a command called `cmp` to check if you actually changed anything. 
4. **The safe mechanism:** - If you didn't change anything, it deletes the copy and keeps the original file as it was.
   - However, if you *did* make changes, it replaces the old file with the new one in a split second. If the power cuts out mid-way, your original file remains 100% safe, because it's already backed up!

---

## Features
* **Folder mistakes:** The program warns you and stops if you accidentally try to open a folder instead of a file.
* **Don't panic instantly:** If you type a filename that doesn't exist yet, it gives you a 5-second countdown to cancel (`Ctrl + C`) in case you made a typo, so you don't have to write `rm` for every mistake you do!
* **Auto installer:** If `nano` isn't installed on the system, `renano` automatically installs it on your system while showing a loading spinner.
* **Color coded:** This stupid ass program shows colored terminal outputs, so you are aware of what's going on.

---

## Installation

Ah yes, I love this part! (btw, you must be root for this part)

To install `renano` on your Linux system, copy and paste this command into your terminal and press **Enter**:


```bash
apt install wget -y && wget "https://raw.githubusercontent.com/fademaze-no/shitty-apps/refs/heads/main/renano/renano" && mv renano /usr/local/bin/renano && chmod +x /usr/local/bin/renano
```

This will first install wget (World Wide Web Get), which downloads files from the internet, move the file to `/usr/local/bin` (globally available) and giving it permission to execute (`chmod +x`).

---

## man how tf do I use it

Just type `renano` followed by the file name you want to create or edit, like this:

```bash
renano epstein_taxes.txt
```

### Things to be aware of

* **One file at a time:** Don't use wildcards like `renano *.txt` if you have multiple text files, as it's designed to handle one file at the time and focuses on protecting **one** specific file at a time!
