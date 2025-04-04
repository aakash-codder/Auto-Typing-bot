import customtkinter as ctk
import pyperclip
import keyboard
import time
import threading

# Setup UI theme
ctk.set_appearance_mode("Dark")
ctk.set_default_color_theme("blue")

app = ctk.CTk()
app.title("Shortcut Typing Tool")
app.geometry("400x420")

# Global states
listener_active = False
current_hotkey = None
typing_speed = 0.06
typing_active = False
typing_thread = None

def type_text_thread():
    """Thread function to type the copied text character by character."""
    global typing_active
    text = pyperclip.paste()
    for char in text:
        if not typing_active:
            break  # Stop typing if shortcut is pressed again
        keyboard.write(char)
        time.sleep(typing_speed)
    typing_active = False  # Reset after finishing or stopping

def type_copied_text():
    """Toggles typing ON/OFF."""
    global typing_active, typing_thread

    if typing_active:
        typing_active = False  # Stop if already typing
        status_label.configure(text="⏹️ Typing Interrupted!")
    else:
        typing_active = True
        typing_thread = threading.Thread(target=type_text_thread, daemon=True)
        typing_thread.start()
        status_label.configure(text="⌨️ Typing Started!")

def start_listener():
    global listener_active, current_hotkey

    shortcut = shortcut_entry.get().strip()
    if not shortcut:
        status_label.configure(text="⚠️ Please enter a valid shortcut.")
        return

    stop_listener()  # Stop any previous listener

    try:
        keyboard.add_hotkey(shortcut, type_copied_text)
        current_hotkey = shortcut
        listener_active = True
        status_label.configure(text=f"✅ Listening: {shortcut} \nCOPY TEXT AND PRESS {shortcut} TO TYPE/STOP")
    except Exception as e:
        status_label.configure(text=f"❌ Error: {e}")

def stop_listener():
    global listener_active, current_hotkey, typing_active
    if current_hotkey:
        keyboard.remove_hotkey(current_hotkey)
        current_hotkey = None
    typing_active = False
    listener_active = False
    status_label.configure(text="🛑 Listener stopped.")

def on_slider_change(value):
    global typing_speed
    typing_speed = round(value, 3)
    slider_label.configure(text=f"Typing Speed: {typing_speed}s/char")

def run_keyboard_wait():
    keyboard.wait()

# Thread to keep keyboard active
listener_thread = threading.Thread(target=run_keyboard_wait, daemon=True)
listener_thread.start()

# UI Elements
ctk.CTkLabel(app, text="🔠 Choose Your Shortcut", font=ctk.CTkFont(size=18)).pack(pady=15)

shortcut_entry = ctk.CTkEntry(app, placeholder_text="e.g. shift+`")
shortcut_entry.insert(0, "ctrl+q")
shortcut_entry.pack(pady=10)

ctk.CTkButton(app, text="▶️ Start Listening", command=start_listener).pack(pady=10)
ctk.CTkButton(app, text="⛔ Stop Listening", command=stop_listener).pack(pady=5)

# Typing speed slider
slider_label = ctk.CTkLabel(app, text=f"Typing Speed: {typing_speed}s/char", font=ctk.CTkFont(size=14))
slider_label.pack(pady=(20, 5))

speed_slider = ctk.CTkSlider(app, from_=0.005, to=0.2, number_of_steps=39, command=on_slider_change)
speed_slider.set(typing_speed)
speed_slider.pack(pady=5, padx=30, fill="x")

# Status label
status_label = ctk.CTkLabel(app, text="No Listener Active", font=ctk.CTkFont(size=14), wraplength=350)
status_label.pack(pady=30)

# Run the app
app.mainloop()
