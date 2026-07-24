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
* 💾 **Local Persistence & JSON Export:** Data is auto-saved to the browser's localStorage. Export the entire plant state as a standard JSON file for offline analysis or import it to another device.  
* 🌍 **Bilingual:** Built-in English and Portuguese (PT) localization.

## **🚀 Quick Start**

1. Download or clone this repository.  
2. Open the digital\_twin\_manual.html (or index.html if renamed) directly in your web browser (Chrome, Safari, Edge, Firefox).  
3. Start mapping your production line\!

## **💡 How to Use (Workflow)**

1. **Map the Line:** Tap **"Add"** to create a new machine. Drag it into position.  
2. **Link Machines:** Click the small "link" icon on a machine, then tap the next machine in the process to connect them.  
3. **Configure the Twin:** Click the machine's name to edit its metadata, name, and add event categories (e.g., Category: "Quality", Options: "OK, Scratch, Burn").  
4. **Log Events:** In the main view, tap a machine to open its "Detail View". Tap the generated category buttons to log timestamped events.  
5. **Extract Data:** Open the Data Settings menu (top left) and click **"Export Data"** to get a .json file containing all structural data and logged events.

## **📊 For Data Scientists**

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

Feel free to fork the repository, tweak the CSS, add new export formats (like CSV), or integrate a REST API call to push the JSON directly to your cloud infrastructure.

**Pull requests are welcome\!**

## **📄 License**

This project is licensed under the MIT License \- see the LICENSE file for details.