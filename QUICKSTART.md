# 🚀 Quick Start Guide

Get Roscoe's medication schedule up and running in minutes!

## For iOS Users (iPhone/iPad)

### Method 1: Direct from Files App (Easiest!)

1. **Download the file:**
   - If you have the file in iCloud Drive, Dropbox, or another cloud service
   - Or receive it via AirDrop/Email

2. **Open in Safari:**
   - Navigate to the `app` folder
   - Tap on `index.html`
   - Choose "Open in Safari" (or tap the share icon → Safari)

3. **Add to Home Screen (Optional but Recommended):**
   - Tap the Share button (square with arrow)
   - Scroll down and tap "Add to Home Screen"
   - Name it "Roscoe Meds"
   - Now you can access it like a real app!

### Method 2: Through a Web Server

If you have the repository cloned locally:

```bash
# Start a simple web server
cd roscoe-med-generator
python3 -m http.server 8000
```

Then on your iOS device:
- Find your computer's IP address (System Settings → Network)
- Open Safari on your iPhone/iPad
- Visit: `http://YOUR_IP_ADDRESS:8000/`
- Add to Home Screen for easy access

### Method 3: GitHub Pages (Easiest - No Download!)

Once GitHub Pages is enabled:
- Visit: `https://jose-vargas-git.github.io/roscoe-med-generator/`
- Works on any device with internet
- Add to Home Screen for offline use

## For Desktop Users

### macOS

```bash
# Option 1: Open directly
open index.html

# Option 2: Serve with Python
python3 -m http.server 8000
# Visit: http://localhost:8000/

# Option 3: Serve with Node.js
npx serve .
# Visit the URL shown in terminal
```

### Windows

```bash
# Option 1: Double-click index.html in File Explorer

# Option 2: Serve with Python
python -m http.server 8000
# Visit: http://localhost:8000/
```

### Linux

```bash
# Option 1: Open with default browser
xdg-open index.html

# Option 2: Serve with Python
python3 -m http.server 8000
# Visit: http://localhost:8000/
```

## Step-by-Step: Generating Your First Schedule

### 1. Open the App
- Launch `index.html` in your browser using any method above
- You'll see the main interface with two buttons at the top

### 2. Click "Generate New Schedule"
A form will appear with the following fields:

**Required:**
- **Start date** – When medication schedule begins
- **End date** – When medication schedule ends

**Optional:**
- **Care location** – e.g., "Happy Paws Boarding" or "Sarah's House"
- **Caregiver name** – e.g., "Sarah Johnson"
- **Additional notes** – Any special instructions for the caregiver
- **Azathioprine on start date** – Check if giving Aza on day 1
- **Azathioprine frequency** – Every other day, every 3 days, etc.
- **Header image** – Upload a photo of Roscoe (optional)
- **Print scale** – Adjust if schedule is too long (60%-120%)

### 3. Fill Out the Form

**Example for a 1-week boarding stay:**

```
Start date: March 15, 2024
End date: March 22, 2024
Care location: Happy Paws Boarding
Caregiver name: Sarah Johnson
Additional notes: Emergency contact: (555) 123-4567. Feed at 8am and 6pm.
☑️ Azathioprine on start date
Azathioprine frequency: Every other day
Print scale: 80
```

### 4. Build & Print

1. Click "Build & Print"
2. The app will:
   - Generate a day-by-day medication checklist
   - Automatically open your browser's print dialog
3. In the print dialog:
   - **Save as PDF** to share digitally
   - **Print** to print on paper
   - Adjust layout if needed

### 5. Share with Caregivers

**On iOS:**
- Save to Files
- Share via Messages, Email, or AirDrop
- Print if you have AirPrint enabled

**On Desktop:**
- Save PDF to your computer
- Email to boarding facility or caregiver
- Print physical copies

## Common Use Cases

### Scenario 1: Weekend Pet Sitter

```
Start: Friday
End: Sunday
Location: Home
Caregiver: Best friend's name
Notes: "Feed at 8am/6pm. Walk 3x daily. Emergency vet: (555) 999-8888"
```

### Scenario 2: Week-Long Boarding

```
Start: July 1
End: July 7
Location: Boarding facility name
Caregiver: Facility staff
Notes: "Prefers wet food mixed with dry. Loves belly rubs!"
```

### Scenario 3: Family Member Care

```
Start: Today
End: +10 days
Location: Mom's house
Caregiver: Mom
Notes: "Roscoe takes Aza every other day - checkboxes show which days!"
```

## Tips for Best Results

### For Mobile (iOS/Android)

1. **Use landscape mode** when filling out the form for better visibility
2. **Add to Home Screen** for quick access
3. **Works offline** once loaded - no internet needed
4. **Touch-friendly** – All buttons and checkboxes are finger-sized
5. **Print scale** – Start with 80%, increase if schedule is long

### For Desktop

1. **Use Chrome or Firefox** for best print results
2. **Print preview** – Check the layout before saving PDF
3. **Landscape mode** not necessary on desktop
4. **Scale adjustment** – 80% usually fits 7-10 days perfectly

### For Printing

1. **Paper size** – 5" wide (portrait), auto height
2. **Color** – Works great in B&W to save ink
3. **Margins** – Pre-configured, but adjustable in print dialog
4. **Quality** – Use "Normal" quality, no need for "Best"

## Troubleshooting

### Print dialog doesn't open?
- Check if pop-ups are blocked
- Click "🖨️ Print / Save PDF" button manually
- Some browsers require permission to print

### Schedule looks too big/small?
- Adjust the "Print scale" slider (60%-120%)
- In print dialog, try "Fit to page"
- 80% is the default and works for most schedules

### Checkboxes don't print?
- They should! Make sure you're saving as PDF
- Try a different browser if issue persists
- Checkboxes work in Safari, Chrome, Firefox

### Image not appearing?
- File must be JPG, PNG, or similar format
- Image loads after clicking "Build & Print"
- Wait a moment before print dialog appears

### Can't open on iOS?
- Make sure file ends with `.html`
- Try opening in Safari specifically
- Can also use Chrome or Firefox on iOS

## Next Steps

- Read [USAGE.md](docs/USAGE.md) for detailed feature explanations
- Check [TECHNICAL.md](docs/TECHNICAL.md) to customize medications
- Share this tool with other pet owners who might need it!

## Questions?

Check the main [README.md](README.md) for more information, or see the detailed [docs/USAGE.md](docs/USAGE.md) guide.

---

**Ready to generate your first schedule?** Open `index.html` and click "Generate New Schedule"! 🐕
