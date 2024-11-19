# Step-by-Step Guide to Setup Hardware

## Step 1: Raspberry Pi Initialization

### Requirements:
1. Raspberry Pi  
2. SD Card  
3. Type-C Cable / Type-C Charger  
4. Ethernet Cable (optional)  

### Raspberry Pi Setup Methods:
#### 1. Wired Setup:
- Requires a micro HDMI cable to get the display directly from the board via the micro HDMI port.

#### 2. Headless Setup:
- Use SSH to access the Raspberry Pi board and configure it to install Remote Desktop Service (RDP).  
- Access the Raspberry Pi's visual interface via remote desktop software such as:
  - **Windows Remote Desktop Connection**
  - **RealVNC** (via IP address).

---
#### Warning:
- Avoid flashing the SD card multiple times or interrupting the flashing process. This could corrupt or permanently damage the card.  
- Ensure strong connections during setup and carefully follow all steps to minimize errors.

### For this project we configured Raspberry pi as Headless Installation.

### Installing Raspberry Pi OS:
1. Download the **Raspberry Pi Imager Tool** from the official website:  
   - **For Windows**:  
     [Raspberry Pi OS using Raspberry Pi Imager](https://www.raspberrypi.com/software/)  
   - **For Linux**:  
     Open a terminal window and type:  
     ```bash
     sudo apt install rpi-imager
     ```
2. Once you’ve installed Imager, launch the application by clicking the Raspberry Pi Imager icon or running `rpi-imager`.
3. Click **Choose OS** and select an operating system to install. The Imager always shows the recommended version of Raspberry Pi OS for your model at the top of the list.

#### For this project, we installed the latest **Raspberry Pi 64-bit Legacy Full**.
- **Alternative**: Raspberry Pi 64-bit Full.  
- **Why Legacy Full?**  
  - Easier and faster access to the Pi Camera Module. The Pi camera feed can be directly accessed by the OpenCV module, whereas other OS versions require manual installation of the `picamera2` library.
  - Faster boot times compared to Raspberry Pi 64-bit Full.
  - Slight performance and FPS improvement with lower CPU usage while using OpenCV video capture.

4. Connect your preferred storage device (e.g., microSD card) to your computer using an external or built-in SD card reader. Then click **Choose Storage** and select your storage device.

#### Warning:
- If you have more than one storage device connected to your computer, ensure you select the correct one! Identify storage devices by size. If unsure, disconnect other devices until you’re certain.

5. Imager will prompt you to apply OS customization. It’s strongly recommended to configure your Raspberry Pi through the OS customization settings. Click **Edit Settings** to open the customization menu.  
   - If skipped, the configuration wizard will prompt you during the first boot.

#### OS Customization Options:
- Preconfigure:
  - A username and password.
  - Wi-Fi credentials.
  - Device hostname.
  - Time zone and keyboard layout.
  - Remote connectivity (e.g., enable SSH).

- If prompted, allow Imager to prefill Wi-Fi credentials from your current network or enter them manually.  
  - **Hostname**: Define a unique hostname to avoid conflicts on networks with multiple Raspberry Pi devices.
  Go to the Services tab then:
  - **Enable SSH**: Must be enabled for headless setup. Use password authentication to prevent unauthorized access.
  ### NOTE : SSH option must be enabled for the headless setup.

6. After completing the customization, click **Save**, then **Yes** to apply the settings.  
7. Click **Write** to begin writing the image to the storage device. Confirm any permissions or admin prompts. The process may take a few minutes.

8. Once completed, insert the SD card into your Raspberry Pi, connect the power cable, and wait a few seconds.

### Congratulations:
You’ve successfully configured your Raspberry Pi! 🎉  
For headless setups, ensure SSH is enabled and test network connectivity.

---

### Boot and Verification:
- Verify the Raspberry Pi has booted properly by observing the LED indicators:  
  - **PWR (red)**: Indicates power is supplied. On later models, it flashes if the voltage drops below 4.63V.  
  - **ACT (green)**: Indicates SD card activity:
    - Flashes during read/write operations.  
    - Flashing patterns indicate errors during boot:
      - 1 flash: Incompatible SD Card.
      - 2 flashes: SD Card cannot be read.
      - 3 flashes: `loader.bin` not found.
      - 4 flashes: `loader.bin` not launched.
      - 5 flashes: `start.elf` not found.
      - 6 flashes: `start.elf` not launched.
      - 7 flashes: `kernel.img` not found.

#### Troubleshooting:
- If boot errors persist, repeat the setup process. Verify that:
  - The SD card is functioning correctly.
  - All steps are followed accurately.

---

