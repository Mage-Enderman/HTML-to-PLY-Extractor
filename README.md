# **SuperSplat HTML to PLY Extractor**

A simple, browser-based tool to extract raw **.ply** (Gaussian Splat) files from self-contained HTML viewers exported by [SuperSplat](https://superspl.at/editor) or PlayCanvas.

## **What is this?**

When you export a scene from a Gaussian Splat editor like SuperSplat using the "Export to Viewer" (HTML) option, the 3D data is embedded directly into the HTML file as a massive Base64 string.  
While this is great for sharing, it makes it difficult to get your original .ply file back if you lose it. This tool reads that HTML file, finds the hidden data, decodes it, and lets you download the original PLY file.

## **Features**

* **100% Client-Side:** No data is uploaded to any server. The extraction happens entirely in your browser memory for maximum privacy and speed.  
* **Large File Support:** Uses chunked memory processing to handle large Base64 strings that might otherwise crash a browser text editor.  
* **Zero Dependencies:** It is a single .html file. No Node.js, Python, or build steps required.

## **How to use**

1. **Download** the index.html file from this repository (or view the [Live Demo](https://mage-enderman.github.io/HTML-to-PLY-Extractor/index.html)).  
2. Open the file in any modern web browser (Chrome, Firefox, Edge, Safari).  
3. **Drag and Drop** your exported viewer HTML file (e.g., scene.html) into the drop zone.  
4. Wait for the extraction to complete.  
5. Click **Download .ply** to save your recovered file.

## **How it works**

The tool parses the uploaded HTML file looking for a specific Data URI pattern used by PlayCanvas/SuperSplat exporters:  
contents: fetch("data:application/ply;base64, ...

It extracts the Base64 string, decodes it into a binary blob using standard browser APIs, and generates a download link.

## **Compatibility**

This tool is designed specifically for:

* HTML files exported from **SuperSplat**.  
* HTML files exported from **PlayCanvas** projects using the splat-transform CLI.

## **📜 License**

MIT License. Feel free to modify or distribute.
