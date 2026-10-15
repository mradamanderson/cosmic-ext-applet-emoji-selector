Because [`cosmic-ext-applet-emoji-selector`](https://github.com/leb-kuchen/cosmic-applet-emoji-selector) is a **COSMIC Panel Applet** rather than a standalone windowed application or background keyboard daemon, it will not appear on your screen or respond to typing until you explicitly add it to your desktop Panel or Dock. Additionally, due to Wayland security protocols in the COSMIC desktop environment, applets use the system clipboard (`smithay-clipboard`) rather than injecting keystrokes directly into active windows.

Follow these steps to enable the applet on your desktop and insert emojis while typing:

---

### **Step 1**
## Open COSMIC Panel Settings
> Open the **COSMIC Settings** application, click on **Desktop** in the left navigation sidebar, and select **Panel** (or **Dock**, if you prefer the selector at the bottom of your screen) from the submenu, as documented in the [System76 Pop!_OS Basics Guide](https://system76.com/support/pop-basics/).
>
> **Verification:** You will see the customization menu containing options for Panel behavior, style, and applet placement.

### **Step 2**
## Add the Emoji Selector Applet to the Panel
> Scroll down to the bottom of the Panel (or Dock) settings page and click **Configure panel applets** (or **Configure dock applets**). Click the **Add applet** button to view the list of installed applets, locate **Emoji Selector**, and add it to the **Start**, **Center**, or **End** section of your bar.
>
> **Verification:** An emoji icon will immediately appear on your top Panel or bottom Dock without requiring a system reboot.

### **Step 3**
## Install the Required Emoji Font
> According to the [cosmic-ext-applet-emoji-selector repository documentation](https://github.com/leb-kuchen/cosmic-applet-emoji-selector), the **Noto Color Emoji** font is required by default to render the icons properly. Ensure it is installed on your Pop!_OS 24.04 system by running:
> ```bash
> sudo apt install fonts-noto-color-emoji
> ```
>
> **Verification:** Click the new Emoji Selector icon on your Panel; the popup grid will display full-color emojis rather than blank squares or missing character symbols.

### **Step 4**
## Select and Paste Emojis When Typing
> When typing in any application, click the **Emoji Selector** icon on your Panel to open the popup window. Browse the categories or use the search bar to find your desired emoji, then click it. Clicking an emoji copies it directly to your system clipboard via [`smithay-clipboard`](https://www.rpmfind.net/linux/RPM/opensuse/ports/tumbleweed/ppc64le/cosmic-ext-applet-emoji-selector-0.1.5+git20240819.13c0a7e-1.10.ppc64le.html). Return to your text field and press **Ctrl + V** (or **Ctrl + Shift + V** inside the COSMIC Terminal) to paste the emoji.
>
> **Verification:** The selected emoji appears in your active text field when pasted.

---

### Troubleshooting Common Issues

* **The applet does not appear in the "Add applet" list:** If the COSMIC Panel daemon has not yet indexed the newly installed `.desktop` file in `/usr/share/applications/`, restart the panel process by running `killall cosmic-panel` in your terminal (it will automatically relaunch), or log out and log back into your COSMIC session.
* **Changing the default font:** If you prefer a different emoji font than Noto Color Emoji, you can modify the `font_family` configuration file located inside `~/.config/cosmic/dev.dominiccgeh.CosmicAppletEmojiSelector/v1/`, as noted in the [GitHub README](https://github.com/leb-kuchen/cosmic-applet-emoji-selector).

Are you able to see and add the **Emoji Selector** inside your COSMIC Panel settings, or is it missing from the available applets list?

---

#### **Select an option below if you need further assistance:**
* **[Applet is missing from list]** — *"The Emoji Selector is not showing up in the Add Applet list in COSMIC Settings. How do I force the panel to detect it?"*
* **[Emojis show as blank boxes]** — *"I added the Emoji Selector to my panel, but some emojis are showing up as blank boxes or monochrome symbols. How do I fix the font configuration?"*
* **[Set up a keyboard shortcut]** — *"Is there a native emoji picker in Linux that I can trigger with a keyboard shortcut instead of clicking the panel applet?"*