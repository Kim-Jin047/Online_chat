# Online Chat for Emotion Regulation Experiment

A real‑time chat application built with Flask and Socket.IO, designed to support emotion‑regulation experiments. Participants can register as users, an administrator can control “speaker turns,” and both human and AI “regulators” can join. After each round, non‑admin participants rate the interaction via an embedded slider UI.

---
## 🌟 Page style
participant：![image](https://github.com/user-attachments/assets/6046e3c6-c90f-4b57-8671-bed92bf547da)
admin：![image](https://github.com/user-attachments/assets/6c3bc1ab-2969-4fe1-b760-63f53303d806)
rating：![image](https://github.com/user-attachments/assets/195351fb-f420-4c46-b1f9-a53217723d8b)


---
## 🚀 Features

- **User Registration**  
  Participants enter a user ID. Special IDs (`管理员`, any name including “调节者”) unlock admin or moderator modes.
- **Real‑Time Messaging**  
  Bi‑directional chat powered by Flask‑SocketIO.
- **Turn‑Based Speaking**  
  Admin selects two users as “speaker1” and “speaker2.” A countdown timer automatically controls when each may speak.
- **Draft Auto‑Save**  
  Participant messages are auto‑saved every few seconds (with on‑screen notice) to prevent data loss.
- **Rating Interface**  
  After each round, non‑admin users provide multi‑dimensional emotion ratings (valence/arousal, perceived helpfulness, etc.) via sliders.
- **AI Integration**  
  A placeholder `AI调节者` can be wired to OpenAI’s API for automated responses.
- **Serial‑Port Hooks**  
  Built‑in `SerialManager` class to interface with external hardware (e.g. fNIRS triggers).

---



## 🛠 Installation

1. **Clone the repo**  
   ```bash
   git clone https://github.com/Kim-Jin047/Online_chat.git
   cd Online_chat

2. **Create & activate a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**

   ```bash
   export OPENAI_API_KEY="your-openai-api-key"
   ```

   * If you don’t use AI, this can be omitted or left empty.

---

## ⚙️ Configuration

* **Serial Port**
  In `app.py`, adjust the default port and baudrate in（If you have external hardware to connect）:

  ```python
  serial_mgr = SerialManager(port_name='COM4', baudrate=9600)
  ```
* **Admin User ID**
  The hard‑coded admin ID is `管理员`. Change `admin_id = '管理员'` in `app.py` if desired.
* **Session History**
  Chat history and ratings are stored in-memory and periodically written to JSON under `./history`. Modify `history_messages` logic in `app.py` to persist elsewhere.

---

## ▶️ Usage

1. **Start the server**

   ```bash
   python app.py
   ```
2. **Open your browser** and navigate to

   ```
   http://localhost:5005
   ```
3. **Register**

   * Enter **任何用户名**.
   * Use **管理员** to unlock the Admin Panel.
   * Use names containing “调节者” (e.g. `AI调节者`) for moderator UI.
4. **Admin Panel** (only for Admin)

   * Select “Speaker 1” and “Speaker 2” from the drop‑downs.
   * Click **开始对话回合** to start the timer and enable speaking turns.
   * The timer will automatically switch or end the turn.
5. **Messaging & Auto‑Save**

   * Moderators and speakers can type during their turn; drafts auto‑save every \~3 s.
   * All messages appear in the shared chat window.
6. **Rating**

   * After each round, the non‑admin participants see a slider UI to rate aspects of the interaction.
   * Click **提交** to send ratings to the server.

---

## 📦 Dependencies

* **Python 3.7+**
* **Flask**
* **Flask‑SocketIO**
* **python‑engineio & python‑socketio**
* **eventlet** (or gevent)
* **openai** (optional, for AI调节者)
* **pyserial** (for `SerialManager`)


---

## ⚖️ License

This project does not currently specify a license. Please contact the author for reuse or redistribution permissions.

---

## ✉️ Contact

For issues or questions, please open an Issue on GitHub or reach out to the repository owner.

```
```
