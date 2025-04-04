# 🔠 Shortcut Typing Tool

A modern Python GUI application that types out your copied text character by character when a custom shortcut key is pressed. Built with [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter), this tool is perfect for automating repetitive typing tasks with a smooth UI and adjustable typing speed.

---

## 🚀 Features

- 🧠 Set your own shortcut key (e.g. `ctrl+q`, `shift+~`)
- 📝 Automatically types out copied text wherever your cursor is
- 🔁 Press shortcut again while typing to stop it instantly
- ⚡ Adjustable typing speed (via slider)
- 🎧 Optional sound feedback support (not enabled in base version)
- 🖤 Dark mode interface

---

## 📸 Preview

> _Coming soon — add screenshots or gifs here!_

---

## 🛠️ Installation

1. **Clone the repo**

```bash
git clone https://github.com/yourusername/shortcut-typing-tool.git
cd shortcut-typing-tool
```

2. **Install the required libraries**

```bash
pip install customtkinter pyperclip keyboard
```

> 🔐 Note: You might need to run your terminal as administrator for `keyboard` to work properly on Windows.

---

## 🧑‍💻 How to Use

1. Run the script:
   ```bash
   python main.py
   ```

2. Set your shortcut key (default is `ctrl+q`)

3. Copy any text (Ctrl+C)

4. Press your shortcut to **start typing** it out

5. Press the shortcut again to **interrupt/stop typing**

6. Adjust typing speed using the slider (lower = faster)

---

## 💡 Built With

- [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter) - Modern UI for Tkinter
- [Pyperclip](https://pypi.org/project/pyperclip/) - Clipboard access
- [Keyboard](https://pypi.org/project/keyboard/) - Global hotkey listener

---

## ⚠️ Notes

- This app works best on **Windows** due to `keyboard` module support.
- May require **admin privileges** depending on your system's security settings.

---

## 📄 License

MIT License © 2025 [Akash](https://github.com/aakash-codder)

---

## 🙌 Contribute

Pull requests are welcome! If you’d like to:
- Add sound effects
- Add a feature to stop the typing using shortcut
- Improve UI responsiveness  
Feel free to fork and send PRs 🚀

---

## 💬 Feedback

connect on [LinkedIn](https://www.linkedin.com/in/aakash101thakur/)
