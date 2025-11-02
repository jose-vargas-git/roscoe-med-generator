# 🐕 Roscoe Medication Schedule Generator

A mobile-friendly web app for generating printable medication schedklist for Roscoe. Perfect for boarding facilities, caregivers, or anyone helping care for your furry friend!

## ✨ Features

- 📱 **Mobile-optimized** – Works perfectly on iOS and Android browsers
- 🖨️ **Print-ready** – Generates clean 5" wide PDFs perfect for posting
- ✅ **Interactive checkboxes** – Check off medications as given
- 📅 **Flexible scheduling** – Set custom date ranges and medication frequencies
- 🎨 **Customizable** – Add caregiver info, notes, and even a photo of Roscoe
- 💾 **No installation** – Runs directly in any web browser
- 📴 **Works offline** – Save the HTML file and use it anywhere

## 🚀 Quick Start

### For Family/Caregivers (Easiest Way)

1. **Open the file on your iOS device:**
   - Navigate to `app/index.html` in Files app
   - Tap to open in Safari (or any browser)
   
2. **Generate your schedule:**
   - Tap "📋 Generate New Schedule"
   - Set start and end dates
   - Fill in caregiver information (optional)
   - Add any special notes
   - Tap "Build & Print"

3. **Print or Save:**
   - Use iOS print dialog to save as PDF
   - Share with caregivers via Messages, Email, or AirDrop
   - Print directly if you have a wireless printer

### For Developers

```bash
# Clone the repository
git clone https://github.com/yourusername/roscoe-med-generator.git
cd roscoe-med-generator

# Open in browser
open app/index.html

# Or serve with Python
python3 -m http.server 8000
# Then visit: http://localhost:8000/app/index.html
```

## 📖 Documentation

- **[QUICKSTART.md](QUICKSTART.md)** – Detailed setup instructions for all users
- **[docs/USAGE.md](docs/USAGE.md)** – Complete usage guide with examples
- **[docs/TECHNICAL.md](docs/TECHNICAL.md)** – Technical details and customization options

## 📋 What's Generated

The app creates a printable checklist with:

- **Date range** – Every day between start and end dates
- **AM medications** – Azathioprine (customizable schedule)
- **PM medications** – Cosequin (daily with dinner)
- **Checkboxes** – Interactive boxes to mark when given
- **Metadata** – Caregiver name, location, special notes
- **Optional photo** – Add a picture of Roscoe at the top

## 💊 Roscoe's Medication Schedule

**Morning (AM with breakfast):**
- Azathioprine ½ tablet (typically every other day)

**Evening (PM with dinner):**
- Cosequin ½ tablet (daily)

*Note: The Azathioprine schedule is customizable in the app (every other day, every 3 days, etc.)*

## 🎯 Use Cases

- **Boarding facilities** – Give them a clear medication schedule
- **Pet sitters** – Keep track of daily medications
- **Friends/family** – Easy checklist when you're away
- **Veterinary care** – Share medication routine with vets
- **Personal tracking** – Keep your own records

## 📁 Project Structure

```
roscoe-med-generator/
├── app/
│   └── index.html          # Main application (mobile-optimized)
├── assets/                 # Optional images/resources
├── docs/
│   ├── USAGE.md           # Detailed usage guide
│   └── TECHNICAL.md       # Technical documentation
├── QUICKSTART.md          # Quick setup guide
└── README.md              # This file
```

## 🔧 Customization

The medication schedule can be easily customized:

1. **Medication types** – Edit the medication names in `index.html`
2. **Frequencies** – Adjust dosing schedules
3. **Layout** – Modify CSS for different print sizes
4. **Branding** – Add your own colors and styling

See [docs/TECHNICAL.md](docs/TECHNICAL.md) for customization instructions.

## 📱 Mobile Browser Support

Tested and optimized for:
- ✅ iOS Safari (iPhone/iPad)
- ✅ Chrome (iOS/Android)
- ✅ Firefox (iOS/Android)
- ✅ Desktop browsers (Chrome, Firefox, Safari, Edge)

## 🖨️ Printing Tips

**On iOS:**
1. Tap "🖨️ Print / Save PDF"
2. Pinch to zoom on preview (optional)
3. Choose "Save to Files" to save as PDF
4. Or select printer to print directly

**On Desktop:**
1. Click "🖨️ Print / Save PDF"
2. Select "Save as PDF" as destination
3. Adjust scale if needed (usually 80% works best)

**Print Size:** 5 inches wide (portrait), variable height based on date range

## ❤️ About Roscoe

This tool was created to help manage Roscoe's daily medication schedule, making it easier for caregivers to ensure he gets his medications on time, every time.

## 📝 Version History

- **v1.0** – Initial release with mobile optimization
  - Touch-friendly interface
  - iOS Safari compatibility
  - Print-to-PDF functionality
  - Custom scheduling options

## 🤝 Contributing

This is a personal project for managing Roscoe's care, but feel free to fork it for your own pet's needs!

## 📄 License

Free to use and modify for personal use.

---

Made with ❤️ for Roscoe 🐕
