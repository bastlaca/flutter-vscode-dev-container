# flutter-vscode-dev-container

**A ready-to-use VS Code devcontainer for Flutter development** using only Docker on the host.  
Supports connecting a **physical Android device via Wi-Fi debugging** and running apps in the browser through Flutter’s built-in web server.  
No need for Android Studio, AVD, or a native emulator – the goal is simplicity, portability, and minimal setup time.

---

## ✨ Benefits

- **No host-side installation chaos** – everything is handled inside the container.
- **Physical device support only** for Android, over Wi-Fi.
- **Web debug** with Chrome + Dart Debug Extension.
- **Fast start** – download, run, pair your phone, and start coding.
- **Cross-platform** – works on macOS, Linux, and Windows with Docker Desktop.

---

## 🔧 Requirements

- Installed [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- VS Code + [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- **Physical Android device** with USB debugging and Wireless debugging enabled
- Chrome browser with Dart Debug Extension

---

## 🌐 Web Server debug

1. **Install Dart Debug Extension for Chrome:**  
   [Dart Debug Extension – Chrome Web Store](https://chrome.google.com/webstore/detail/dart-debug-extension/eljbmlghnomdjgdjmbdekegdkbabckhm)
2. In VS Code, choose **Web Server** from the debug list.
3. Launch the project (`Launch`).
4. In Chrome, click the **Dart Debug Extension** icon.

> ⚠ **Note:** Web debug does **not** work with Flutter versions 3.32.0–3.32.8.

---

## 📱 Android – Physical device only (Wi-Fi debug)

No emulator required. The host does not need to run ADB, avoiding conflicts.

**Steps:**
1. **On the phone, enable**:
   - *USB debugging*
   - *Wireless debugging* (in Developer options)
2. On the phone, go to **Wireless debugging** → *Pair device with pairing code*
3. In the container, pair:
   ```bash
   adb pair <phone-ip>:<pair-port>
   # Example1: adb pair 192.168.1.42:37123
   # Example2: adb pair 192.168.1.42:37123 123456
   ```
4. After pairing, connect:
   ```bash
   adb connect <phone-ip>:<connect-port>
   adb devices
   ```
5. If the device appears, run:
   ```bash
   flutter run -d <device-id>
   ```

---

## 🛠 Troubleshooting

- **VS Code doesn’t see the device:**  
  In Command Palette: `>Dart: Restart Analysis Server`
- **Regenerate ADB keys** (if pairing issues occur):
  ```bash
  rm -f ~/.android/adbkey ~/.android/adbkey.pub
  adb keygen ~/.android/adbkey
  ```

---

# flutter-vscode-dev-container (HU)

**Egy készre csomagolt VS Code devcontainer Flutter fejlesztéshez**, amely kizárólag Docker-t használ a hoston.  
Támogatja a **fizikai Android eszköz Wi-Fi debuggal** való csatlakoztatását, valamint a webes futtatást a Flutter saját web szerverén keresztül.  
Nincs szükség Android Studio-ra, AVD-re vagy natív emulátorra – a cél az egyszerű, hordozható és minimális beállítási idő.

---

## ✨ Előnyök

- **Nincs host oldali telepítési káosz** – mindent a konténer kezel.
- **Kizárólag fizikai eszköz támogatás** Androidra, Wi-Fi-n keresztül.
- **Web debug** Chrome + Dart Debug Extension segítségével.
- **Gyors indulás** – letöltöd, futtatod, párosítod a telefont, és már fejlesztesz is.
- **Platformfüggetlen** – macOS, Linux és Windows Docker Desktopon is működik.

---

## 🔧 Előfeltételek

- Telepített [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- VS Code + [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- **Fizikai Android eszköz**, amin engedélyezve van az USB és a Wireless Debugging
- Chrome böngésző Dart Debug Extension-nel

---

## 🌐 Web Server debug

1. **Telepítsd a Dart Debug Extension-t Chrome-ba:**  
   [Dart Debug Extension – Chrome Web Store](https://chrome.google.com/webstore/detail/dart-debug-extension/eljbmlghnomdjgdjmbdekegdkbabckhm)
2. VS Code debug listából válaszd a **Web Server** opciót.
3. Indítsd el a projektet (`Launch`).
4. Chrome-ban kattints rá a **Dart Debug Extension** ikonra.

> ⚠ **Figyelem:** a 3.32.0–3.32.8 verzióval **nem működik** a webes debug.

---

## 📱 Android – Csak fizikai eszköz (WiFi debug)

Ebben a felállásban **nincs szükség emulátorra**. A hoston nem kell ADB-nek futnia, és nem ütközik semmilyen háttérfolyamat.

**Lépések:**
1. **Engedélyezd a telefonon**:
   - *USB debugging*
   - *Wireless debugging* (Fejlesztői beállításokban)
2. Telefonon a **Wireless debugging** menüben válaszd: *Pair device with pairing code*
3. Konténerben párosítsd:
   ```bash
   adb pair <telefon-ip>:<pair-port>
   # Példa1: adb pair 192.168.1.42:37123
   # Példa2: adb pair 192.168.1.42:37123 123456
   ```
4. Párosítás után csatlakozz:
   ```bash
   adb connect <telefon-ip>:<connect-port>
   adb devices
   ```
5. Ha itt látod az eszközt, mehet:
   ```bash
   flutter run -d <device-id>
   ```

---

## 🛠 Hibakeresési tippek

- **VS Code nem látja az eszközt:**  
  Parancspalettában: `>Dart: Restart Analysis Server`
- **ADB kulcs újragenerálás** (ha párosításnál gond van):
  ```bash
  rm -f ~/.android/adbkey ~/.android/adbkey.pub
  adb keygen ~/.android/adbkey
  ```
