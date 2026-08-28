# PhotonDrop

<div align="center">

<img src="assets/logo.png" width="110" alt="PhotonDrop 3D Logo" />

### **Zero-Network, Air-Gapped Data Transfer**
*Send files, photos, and text using only light. No internet, no Wi-Fi, no Bluetooth.*

[![Platform: iOS & Web](https://img.shields.io/badge/Platform-iOS%20%7C%20Web-00d2ff?style=for-the-badge&logo=apple)](https://github.com/ummugulsunn)
[![Security: Air-Gapped](https://img.shields.io/badge/Security-100%25%20Air--Gapped-10b981?style=for-the-badge&logo=shield)](https://github.com/ummugulsunn)
[![Protocol: Fountain Codes](https://img.shields.io/badge/Engine-LT%20Fountain%20Codes-6366f1?style=for-the-badge)](https://github.com/ummugulsunn)

</div>

---

## What is PhotonDrop?

Imagine you need to transfer a highly confidential document, a crypto wallet key, or a private photo to a device that is completely disconnected from the world. No Wi-Fi, no cellular data, no Bluetooth, and no USB cables (which can carry malware). 

**How do you send data to a device that is totally isolated?**

**PhotonDrop** solves this by turning your data into **light**. It takes any file, slices it into microscopic pieces, and streams those pieces as a high-speed animation of QR codes on your screen. The receiving device simply points its camera at the screen, "recording" the flashing lights, and seamlessly rebuilds the original file instantly. 

100% Offline. 100% Air-Gapped. 100% Secure.

---

## Who Is This For?

- **Cybersecurity Professionals:** Transferring logs or configurations to air-gapped (isolated) secure servers.
- **Crypto Holders:** Moving private keys or seed phrases to offline "cold storage" devices without exposing them to the internet.
- **Journalists & Whistleblowers:** Sharing sensitive evidence between phones in hostile environments where networks are monitored or jammed.
- **Enterprise & Government:** Moving data safely into highly restricted facilities where wireless signals are strictly prohibited.

---

## How It Works (User Experience)

Using PhotonDrop is as easy as taking a video:

1. **Select:** Choose a file, photo, or type a text snippet on the sender device (Web or Mobile).
2. **Stream:** The sender's screen begins flashing a mesmerizing, high-speed QR animation.
3. **Scan:** Open the PhotonDrop app on the receiving phone and point the camera at the flashing screen. 
4. **Receive:** Within seconds, the file appears on the receiver's screen, ready to be previewed and saved!

<div align="center">
  <table>
    <tr>
      <td align="center" width="50%">
        <img src="assets/preview_image.png" width="300px" alt="Image Transfer Preview" /><br/>
        <b>Photo / Media Instant Preview</b>
      </td>
      <td align="center" width="50%">
        <img src="assets/preview_text.png" width="300px" alt="Text Snippet Preview" /><br/>
        <b>Text Snippet & Secure Key Stream</b>
      </td>
    </tr>
  </table>
</div>

---

## Under The Hood: Technical Architecture

For the engineers and security researchers, here is how PhotonDrop achieves lossless data transfer over an unreliable optical medium (a camera lens) without any network protocols (like TCP/IP).

### 1. Fountain Code Generation (The "Waterfall" Algorithm)
In traditional networking, if a packet is lost, the receiver asks the sender to re-transmit it. In our optical transfer, the camera cannot talk back to the screen to say "I missed frame #45". 
To solve this, PhotonDrop uses **Luby Transform (LT) Fountain Codes**:
- The file is divided into equal chunks.
- Instead of showing chunks sequentially (1, 2, 3...), the sender mathematically mixes them using the **XOR** operator.
- The sender generates an **infinite, non-repeating stream** of these combinations (like droplets from a water fountain).
- The receiving camera just needs to catch *any* random subset of these droplets. It doesn't matter if you blink, move the camera, or glare hits the screen; missed frames are mathematically irrelevant. Once enough droplets are caught, the original file is reconstructed using Gaussian Elimination.

### 2. Native iOS Lossless Byte Recovery
Standard mobile QR scanners (like your phone's default camera) try to read QR codes as "Text". This instantly destroys and corrupts raw binary data like encrypted files or images. 
PhotonDrop bypasses standard scanner libraries entirely. We engineered a custom **Swift patch** directly into iOS `AVFoundation`, intercepting the camera at the hardware level to extract raw **ISO-8859-1 (Latin1)** bytes with absolute zero corruption, streaming them securely into our JavaScript engine.

### 3. File Packing & Encryption (DCF2)
Every file is packaged into a proprietary **Decimen Container Format 2 (DCF2)**. This container holds the exact file name, type, and size. Optionally, the entire payload is encrypted using military-grade **AES-256-GCM** cryptography before being turned into light.

### 4. Zero-Storage Preview
Once the receiver mathematically solves the file, it undergoes a strict **SHA-256 cryptographic checksum** validation. The file is then rendered instantly in the device's memory (RAM) as a beautiful preview. The file is *never* written to the physical storage of the phone unless the user explicitly taps "Save".

---

## Technology Stack

| Layer | Technologies & Implementations |
| :--- | :--- |
| **Mobile Application** | React Native (Expo 51), TypeScript, Custom Hermes UTF-8 Polyfill Engine |
| **Native iOS Core** | Swift, AVFoundation, VisionKit, CoreImage Codeword Descriptors |
| **Web Portal** | Vite, TypeScript, Canvas QR Streamer, Web Workers |
| **Data Engine** | Luby Transform (LT), Pako GZIP, js-sha256, Web Crypto API |
| **Design System** | Custom Dark Glassmorphism, Haptic Feedback, Modern Phosphor & Lucide Accents |

---

## Live Demo & Reference

- **Try The Sender Portal:** [PhotonDrop Web Interface](https://ummugulsunn.github.io/photondrop-app)
- **Repository Type:** Private Engineering Portfolio
- **Lead Developer & Architect:** Ümmügülsün ([@ummugulsunn](https://github.com/ummugulsunn))

---

<div align="center">
  <sub>© 2026 PhotonDrop • Engineered for extreme security and air-gapped environments.</sub>
</div>
