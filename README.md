# 🔓 Web Excel Protection Remover

Standalone web application to remove Excel (.xlsx) file protections directly in the browser, without requiring a server or installations.

## 📋 Description

This web app replicates the functionality of the VBA macro "SbloccaExcelCompleto_NETZIP" in a single HTML page. It uses modern JavaScript and the JSZip library to manipulate the internal structure of .xlsx files, removing:

- ✅ Sheet protections (sheetProtection)
- ✅ Workbook structure protection (workbookProtection)
- ✅ Window locking (lockWindows)
- ✅ Locked cells (locked="1" in styles)

**Does NOT remove:**
- 🔒 VBA passwords (disabled by request)

## ⚠️ Important Notice

> **RESPONSIBLE USE** - This tool should ONLY be used in emergency situations and with the file owner's consent. Usage must comply with company policies and internal regulations.

## 🚀 Features

- **No installation required** - Works directly in your browser
- **Privacy guaranteed** - All processing happens locally, no data is sent to external servers
- **Intuitive interface** - Drag & drop file upload
- **Real-time feedback** - Progress bar and detailed report
- **Compatible** - Works with Chrome, Edge, Firefox and other modern browsers
- **Single file** - All code in one `index.html` file

## 📦 Installation

### Option 1: Local execution (recommended)

1. Download or clone this repository
2. Open the `index.html` file with a modern browser
3. Start using the application

```bash
# Clone the repository
git clone [https://github.com/your-username/web-excel-protection-remover.git](https://github.com/your-username/web-excel-protection-remover.git)

# Navigate to the folder
cd web-excel-protection-remover

# Open with default browser
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

### Option 2: Static hosting

You can host this application on any static hosting service:

- **GitHub Pages**
- **Netlify**
- **Vercel**
- **Apache/Nginx** local server

## 💻 Usage

1. **Open** the `index.html` file in your browser
2. **Drag** a `.xlsx` file into the designated area or click to select
3. **Click** the "🚀 Unlock Excel File" button
4. **Wait** for processing to complete
5. **Download** the unlocked file with the green button

The unlocked file will be saved with the suffix `_sbloccato.xlsx` (e.g., `report_sbloccato.xlsx`).

## 🛠️ Technologies

- **HTML5** - Page structure
- **CSS3** - Styling and responsive layout
- **JavaScript ES6+** - Application logic
- **JSZip** - Library for ZIP file manipulation (loaded from CDN)

## 📁 Repository Structure


web-excel-protection-remover/
├── index.html # Complete web application
├── README.md # This file
└── LICENSE # License file


## 🔧 How It Works

The application follows these steps:

1. **File reading** - The .xlsx file is read as ArrayBuffer
2. **Decompression** - JSZip extracts the ZIP content
3. **XML modification** - Internal XML files are modified:
   - `xl/worksheets/sheet*.xml` - Removal of `<sheetProtection>` tags
   - `xl/workbook.xml` - Removal of `<workbookProtection>` tags
   - `xl/styles.xml` - Removal of `locked="1"` and `applyProtection="1"` attributes
4. **Recompression** - Content is compressed into a new .xlsx file
5. **Download** - The unlocked file is made available for download

## 🔒 Security and Privacy

- **No upload** - Files are never sent to external servers
- **Local processing** - Everything happens in the user's browser
- **No tracking** - No data or usage statistics are collected
- **Open source** - Code is fully visible and verifiable

## ⚠️ Limitations

- Only works with `.xlsx` files (not legacy `.xls`)
- Requires a modern browser with ES6 and File API support
- JSZip library is loaded from CDN (requires internet connection on first load)
- Very large files (>100MB) may take longer to process

## 🔄 Differences from VBA Version

| Feature | VBA Version | Web Version |
|---------|-------------|-------------|
| Platform | Excel Windows | Any modern browser |
| Installation | Requires Excel | None |
| Processing | Local (VBA + PowerShell) | Local (JavaScript) |
| Dependencies | .NET ZipFile, PowerShell | JSZip (CDN) |
| Interface | Windows MessageBox | Modern Web UI |
| Drag & Drop | ❌ No | ✅ Yes |
| Fully offline | ✅ Yes | ⚠️ Partially (CDN) |

## 🌐 Fully Offline Mode

To use the application without internet connection, download the JSZip library and include it directly in the HTML file:

1. Download `jszip.min.js` from: https://cdnjs.com/libraries/jszip
2. Save the file in the same folder as `index.html`
3. Replace the line:
   ```html
   <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
   ```
   with:
   ```html
   <script src="jszip.min.js"></script>
   ```

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a branch for your feature (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is distributed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Bruno Benevolo**

Developed for internal company use and community.

## 🙏 Acknowledgments

- [JSZip](https://stuk.github.io/jszip/) - Library for ZIP file manipulation in JavaScript
- VBA/Excel community for inspiration from the original macro

## 📞 Support

For issues, questions, or suggestions, please open an [Issue](https://github.com/your-username/web-excel-protection-remover/issues) in the repository.

---

**Note:** This project was created for educational and emergency purposes. Use responsibly and in compliance with company policies and privacy regulations.