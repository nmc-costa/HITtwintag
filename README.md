© 2021 nmc-costa. All Rights Reserved. simplifyhit™ is a trademark of nmc-costa.

# **🏭 Digital Twin Annotator**

A lightweight, zero-dependency, single-file HTML web application designed to visually map manufacturing processes, digitalize domain knowledge, and manually log events on the factory floor.

Built for **Data Scientists, Industrial Engineers, and Operators**, this tool bridges the gap between physical production lines and digital data collection without requiring any backend, database, or internet connection.

## **✨ Key Features**

* 📦 **Zero Backend & Zero Dependencies:** It's just one HTML file. No npm, no servers, no databases. Open it in any modern browser.  
* 📱 **Mobile & Tablet First:** Designed for touch interfaces on the factory floor. Features smooth canvas panning and intuitive drag-and-drop.  
* 🔍 **Semantic Zoom (Eagle vs. Detail View):**  
  * **Eagle View:** A macro-level, ultra-compact map of the production line.  
  * **Detail View:** Tap a machine to focus, expand its interface, and instantly log events with large, operator-friendly buttons.  
* 🔗 **Visual Process Flow:** Easily link machines to create logical production paths (Flowchart style).  
* ⚙️ **Custom Metadata:** Add custom Key-Value pairs (e.g., PLC\_ID: 123, Target\_Temp: 180ºC) to any machine.  
* 🏷️ **Custom Categorization:** Define specific defect types per machine (e.g., OK, NOK, Bubble, Misaligned).  
* 💾 **Local Persistence & JSON Export/Import:** Data is auto-saved to the browser's localStorage. Export the entire plant state as a standard JSON file for offline analysis or import it to another device via **File Picker**, **Copy/Paste**, or **Drag & Drop**.  
* 🌍 **Bilingual:** Built-in English and Portuguese (PT) localization.
* 📲 **Android-Friendly:** Multiple import methods optimized for mobile devices, including a copy/paste modal that works reliably on all platforms.

## **🚀 Quick Start**

1. Download or clone this repository.  
2. Open the digital\_twin\_manual.html (or index.html if renamed) directly in your web browser (Chrome, Safari, Edge, Firefox).  
3. Start mapping your production line\!

## **💡 How to Use (Workflow)**

### **Creating & Mapping**
1. **Map the Line:** Tap **"Add Machine"** to create a new machine. Drag it into position.  
2. **Link Machines:** Click the small "link" icon on a machine, then tap the next machine in the process to connect them.  
3. **Configure the Twin:** Click the machine's name to edit its metadata, name, and add event categories (e.g., Category: "Quality", Options: "OK, Scratch, Burn").  
4. **Log Events:** In the main view, tap a machine to open its "Detail View". Tap the generated category buttons to log timestamped events.  

### **Data Export & Import**
5. **Export Data:** Open the Settings menu (☰) and click **"Export Data (JSON)"** to download a JSON file with all structural data and logged events.

6. **Import Data:** Use any of the three methods:
   * **📄 Import from File:** Click the file picker button to select a previously exported JSON file.
   * **📋 Paste JSON:** Click "Paste JSON", paste your exported data into the textarea, and click "Import". *(Recommended for Android)*
   * **🎯 Drag & Drop:** On desktop browsers, drag a JSON file directly onto the canvas to import it.

## **� Data Import Methods**

The app supports **three flexible import methods** to work seamlessly across all devices and browsers:

| Method | Platform | Use Case |
|--------|----------|----------|
| **📄 File Picker** | Desktop, Android, iOS | Select JSON files from your device storage. Works on most modern browsers. |
| **📋 Copy/Paste** | All platforms | Paste JSON text directly into a modal textarea. **Best for Android & unreliable file systems.** Opens a dedicated dialog box. |
| **🎯 Drag & Drop** | Desktop (Chrome, Firefox, Edge) | Drag a JSON file directly onto the canvas. Quick and intuitive for desktop workflows. |

### **Example Import Workflow (Android)**
1. On your desktop, export the JSON via **"Export Data"**
2. Share or copy the JSON text
3. On Android, open the app and tap ☰ → **"Paste JSON"**
4. Paste the JSON into the text area
5. Click **"Import"** to load your layout and data

---

## **�📊 For Data Scientists**

The main goal of this tool is to quickly generate structural labels and domain knowledge data that can be parsed by Python/Pandas for **Predictive Maintenance** or **Anomaly Detection** models.

The exported JSON structure looks like this:

```
{
  "nodes": [
    {
      "id": "m1_xyz",
      "name": "Lamination Press",
      "x": 150,
      "y": 200,
      "metadata": {
        "ID": "LAM_01"
      },
      "categories": [
        {
          "id": "cat_1",
          "name": "Defect Type",
          "options": ["OK", "Bubble", "Misaligned"],
          "events": [
            {
              "timestamp": "2026-07-24T10:15:30.123Z",
              "value": "Bubble"
            }
          ]
        }
      ]
    }
  ],
  "edges": [
    {
      "source": "m1_xyz",
      "target": "m2_abc"
    }
  ],
  "ui": {
    "viewMode": "detail",
    "focusedMachine": "m1_xyz"
  }
}
```

## **🛠️ Customization & Contribution**

Because the entire app is contained within a single file using Tailwind CSS via CDN and vanilla JavaScript, customizing it is extremely simple.

Feel free to fork the repository, tweak the CSS, add new export formats (like CSV), extend the import methods, or integrate a REST API call to push the JSON directly to your cloud infrastructure.

**Recent additions:**
- Multi-method data import (file, paste, drag-drop)
- Android-optimized copy/paste modal
- Full i18n support for new UI elements

**Pull requests are welcome\!**

## **📄 License**

This project is licensed under the MIT License \- see the LICENSE file for details.