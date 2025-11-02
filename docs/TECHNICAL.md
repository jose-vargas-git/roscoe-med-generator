# 🔧 Technical Documentation

Technical details, customization guide, and developer information for the Roscoe Medication Schedule Generator.

## Table of Contents

1. [Architecture Overview](#architecture-overview)
2. [Technology Stack](#technology-stack)
3. [File Structure](#file-structure)
4. [Customization Guide](#customization-guide)
5. [Mobile Optimization](#mobile-optimization)
6. [Print Optimization](#print-optimization)
7. [Browser Compatibility](#browser-compatibility)
8. [Troubleshooting](#troubleshooting)
9. [Contributing](#contributing)

## Architecture Overview

### Design Philosophy

The app is built as a **single-file, zero-dependency web application**:

- ✅ No external libraries or frameworks
- ✅ No build process required
- ✅ Works completely offline
- ✅ Pure HTML + CSS + vanilla JavaScript
- ✅ Mobile-first, responsive design
- ✅ Progressive enhancement approach

### Why Single File?

1. **Portability** – Easy to share via any method
2. **Simplicity** – No installation or dependencies
3. **Reliability** – No CDN failures or version conflicts
4. **Offline-first** – Works anywhere, anytime
5. **Transparency** – All code visible and auditable

## Technology Stack

### Core Technologies

- **HTML5** – Semantic markup, dialog element
- **CSS3** – Grid, Flexbox, CSS Variables, Print media queries
- **JavaScript (ES6+)** – Vanilla JS, no frameworks
- **Web APIs** – FileReader, Date, Print API

### Key Features

1. **CSS Grid** – Responsive layout
2. **CSS Custom Properties** – Easy theming
3. **Print Media Queries** – Optimized PDF output
4. **FileReader API** – Client-side image processing
5. **HTML5 Dialog** – Native modal dialogs
6. **Local Storage** – (Not currently used, but could be added)

### Browser APIs Used

```javascript
// Date manipulation (built-in)
new Date()
Date.prototype.toLocaleDateString()

// File reading
FileReader()
reader.readAsDataURL()

// Printing
window.print()

// Modal dialogs
HTMLDialogElement.showModal()
HTMLDialogElement.close()
```

## File Structure

### Project Layout

```
roscoe-med-generator/
│
├── index.html                 # Main application (all-in-one)
├── assets/                    # Optional assets
│   └── (user images go here)
├── docs/
│   ├── USAGE.md              # User guide
│   └── TECHNICAL.md          # This file
├── .gitignore                # Git ignore rules
├── README.md                 # Project overview
└── QUICKSTART.md             # Quick setup guide
```

### index.html Structure

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Metadata and viewport -->
    <style>
      /* CSS Variables */
      /* Print styles */
      /* Mobile styles */
      /* Component styles */
    </style>
  </head>
  <body>
    <!-- Toolbar (no-print) -->
    <!-- Schedule sheet (printable) -->
    <!-- Configuration dialog -->
    <script>
      /* Pure JavaScript */
    </script>
  </body>
</html>
```

## Customization Guide

### Changing Medication Names

**Location:** Lines 303-304 and 324 in `index.html` (root folder)

**Example:** Change "Azathioprine" to "Prednisone":

```javascript
// Find this line (around line 303):
amText.textContent = giveAza ? 'Azathioprine ½ tab' : '—';

// Change to:
amText.textContent = giveAza ? 'Prednisone ½ tab' : '—';
```

**For PM medication (around line 324):**

```javascript
// Find:
pmText.textContent = 'Cosequin ½ tab';

// Change to:
pmText.textContent = 'Glucosamine 1 tab';
```

### Adding Additional Medications

To add a third daily medication, you'll need to:

1. **Add a new column to the table header:**

```html
<!-- Around line 130 -->
<thead>
  <tr>
    <th class="dateCell">Date</th>
    <th>AM (Breakfast)</th>
    <th>PM (Dinner)</th>
    <th>Evening (Bedtime)</th> <!-- NEW -->
  </tr>
</thead>
```

2. **Add generation logic in the build() function:**

```javascript
// After the PM cell code (around line 334), add:
const eveningTd = document.createElement('td');
const eveningRow = document.createElement('div');
eveningRow.className = 'slotRow';

const eveningLabel = document.createElement('span');
eveningLabel.className = 'slotLabel';
eveningLabel.textContent = 'EVE';
eveningRow.appendChild(eveningLabel);

const eveningText = document.createElement('span');
eveningText.className = 'medText';
eveningText.textContent = 'Medication Name 1 tab';
eveningRow.appendChild(eveningText);

const eveningCheck = document.createElement('label');
eveningCheck.className = 'checkBox';
const eveningInput = document.createElement('input');
eveningInput.type = 'checkbox';
eveningInput.setAttribute('aria-label', `Evening medication for ${formatDateNice(d)}`);
eveningCheck.appendChild(eveningInput);
eveningRow.appendChild(eveningCheck);

eveningTd.appendChild(eveningRow);
tr.appendChild(eveningTd);
```

### Changing Print Size

**Location:** CSS `@page` rule (line 18)

```css
/* Current: 5 inches wide */
@page { size: 5in auto; margin: 0.5in; }

/* Change to 8.5" (letter width) */
@page { size: 8.5in auto; margin: 0.75in; }

/* Change to A4 */
@page { size: 210mm 297mm; margin: 15mm; }
```

Also update the CSS variable:

```css
:root {
  --page-w: 5in;  /* Change this too */
}
```

### Customizing Colors

**Location:** CSS `:root` section (lines 8-16)

```css
:root {
  --ink: #111;           /* Main text color */
  --muted: #6b7280;      /* Secondary text */
  --line: #e5e7eb;       /* Border colors */
  --page-w: 5in;         /* Page width */
  --gap: 12px;           /* Spacing */
  --radius: 14px;        /* Border radius */
  --scale: 0.8;          /* Default scale */
  --touch-target: 44px;  /* Button minimum size */
}
```

**Example:** Blue theme:

```css
:root {
  --ink: #1e3a8a;           /* Dark blue */
  --muted: #60a5fa;         /* Light blue */
  --line: #bfdbfe;          /* Pale blue */
}
```

### Adding New Frequency Options

**Location:** Dialog HTML (around line 180) and JavaScript (line 281)

```html
<!-- Add option to select -->
<select id="azaEvery">
  <option value="2" selected>Every other day</option>
  <option value="3">Every 3 days</option>
  <option value="4">Every 4 days</option>
  <option value="5">Every 5 days</option> <!-- NEW -->
</select>
```

No JavaScript changes needed – it already handles any number!

### Changing Default Date Range

**Location:** JavaScript initialization (lines 244-247)

```javascript
// Current: Today + 7 days
const today = new Date();
startEl.value = toLocalInputValue(today);
endEl.value = toLocalInputValue(addDays(today, 6));

// Change to: Tomorrow + 14 days
const tomorrow = addDays(new Date(), 1);
startEl.value = toLocalInputValue(tomorrow);
endEl.value = toLocalInputValue(addDays(tomorrow, 13));
```

### Customizing Footer Text

**Location:** Footer HTML (lines 138-141)

```html
<footer>
  <strong>Medication Details:</strong><br>
  AM – Azathioprine ½ tab (per schedule). PM – Cosequin ½ tab daily with dinner.
  <!-- Customize this text as needed -->
  <div id="metaLine" class="note"></div>
  <div id="notesLine" class="note"></div>
</footer>
```

## Mobile Optimization

### Touch-Friendly Sizing

All interactive elements meet accessibility guidelines:

```css
:root {
  --touch-target: 44px;  /* Apple HIG recommendation */
}

.btn {
  min-height: var(--touch-target);
  padding: 12px 16px;
}

.checkBox {
  width: 28px;
  height: 28px;
}
```

### iOS Safari Specific

**Prevent zoom on input focus:**

```css
input, select, textarea {
  font-size: 16px;  /* Prevents iOS auto-zoom */
}
```

**Disable tap highlight:**

```css
* {
  -webkit-tap-highlight-color: rgba(0,0,0,0.05);
}
```

**Double-tap zoom prevention:**

```javascript
let lastTap = 0;
document.addEventListener('touchend', (e) => {
  const now = Date.now();
  if (now - lastTap < 300) {
    e.preventDefault();
  }
  lastTap = now;
});
```

### Responsive Breakpoints

```css
/* Stack form fields on small screens */
@media (max-width: 480px) {
  .grid-2 {
    grid-template-columns: 1fr;
  }
}
```

## Print Optimization

### Print Media Query

```css
@media print {
  /* Exact color reproduction */
  body {
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
  }
  
  /* Hide non-essential elements */
  .no-print {
    display: none !important;
  }
  
  /* Remove scale transform */
  .sheet {
    transform: scale(1) !important;
    box-shadow: none;
  }
  
  /* Hide dialogs */
  dialog[open] {
    display: none !important;
  }
}
```

### Page Size Configuration

```css
@page {
  size: 5in auto;      /* 5" wide, auto height */
  margin: 0.5in;       /* Half-inch margins */
}
```

### Print-Friendly Checkboxes

Checkboxes are styled to print as empty boxes:

```css
.checkBox {
  border: 2px solid #9aa3ad;
  /* Prints as visible outline */
}
```

## Browser Compatibility

### Tested Browsers

| Browser | Version | Status |
|---------|---------|--------|
| Safari (iOS) | 14+ | ✅ Fully supported |
| Chrome (iOS) | 90+ | ✅ Fully supported |
| Safari (macOS) | 14+ | ✅ Fully supported |
| Chrome (Desktop) | 90+ | ✅ Fully supported |
| Firefox | 88+ | ✅ Fully supported |
| Edge | 90+ | ✅ Fully supported |

### Feature Support

- **Dialog element**: Supported in all modern browsers
- **CSS Grid**: Supported (fallback: flexbox)
- **CSS Variables**: Supported (no fallback needed)
- **FileReader API**: Supported (image upload)
- **Print API**: Universal support

### Fallbacks

**For older browsers without dialog support:**

```javascript
try {
  dlg.showModal();
} catch(e) {
  dlg.setAttribute('open', '');
}
```

## Troubleshooting

### Common Issues

#### 1. Print Dialog Doesn't Open

**Cause:** Browser is blocking pop-ups

**Solution:**
- Allow pop-ups for the site
- Manually click "Print / Save PDF" button
- Check browser console for errors

#### 2. Checkboxes Don't Print

**Cause:** Browser print settings

**Solution:**
- Ensure "Background graphics" is enabled
- Try "Save as PDF" instead of printing directly
- Check CSS print media queries are working

#### 3. Image Doesn't Load

**Cause:** File format not supported, or file too large

**Solution:**
- Use JPG or PNG format
- Compress images to < 5MB
- Check browser console for errors
- Ensure FileReader API is supported

#### 4. Layout Breaks on Mobile

**Cause:** Viewport settings or CSS issues

**Solution:**
- Check viewport meta tag is present
- Test in Safari (iOS), not Chrome
- Clear browser cache
- Check for CSS conflicts

#### 5. Dialog Won't Close on iOS

**Cause:** iOS Safari dialog implementation

**Solution:**
- Use the Cancel button instead of backdrop
- Fallback code handles this automatically

### Debug Mode

To enable debugging, open browser console (F12) and add:

```javascript
// Add to script section
console.log('App loaded');
console.log('Start date:', startEl.value);
console.log('End date:', endEl.value);
```

### Performance

**Load time:** < 100ms (single file, no network requests)
**Print time:** < 1 second for 30-day schedule
**Memory:** < 5MB for typical usage
**Image processing:** < 500ms for < 5MB images

## Contributing

### Code Style

- **Indentation:** 2 spaces
- **Quotes:** Single quotes for JavaScript
- **Semicolons:** Yes (JavaScript)
- **CSS:** Alphabetical properties

### Adding Features

1. Test on iOS Safari first (primary target)
2. Ensure print output looks correct
3. Maintain offline functionality
4. Keep file size minimal
5. Document changes in comments

### Testing Checklist

- [ ] Works on iOS Safari (iPhone)
- [ ] Works on iOS Safari (iPad)
- [ ] Works on Chrome (desktop)
- [ ] Works on Firefox
- [ ] Print preview looks correct
- [ ] PDF output is correct
- [ ] All form validations work
- [ ] Image upload works
- [ ] Offline functionality intact
- [ ] Touch targets meet size requirements

### Submitting Changes

1. Test thoroughly on multiple devices
2. Update relevant documentation
3. Keep changes minimal and focused
4. Maintain single-file architecture
5. Don't add external dependencies

## Advanced Customization

### Adding Local Storage

To remember user preferences:

```javascript
// Save to localStorage
function saveSettings() {
  localStorage.setItem('roscoeMedSettings', JSON.stringify({
    location: locEl.value,
    caregiver: cgEl.value,
    azaEvery: azaEveryEl.value
  }));
}

// Load from localStorage
function loadSettings() {
  const saved = localStorage.getItem('roscoeMedSettings');
  if (saved) {
    const settings = JSON.parse(saved);
    locEl.value = settings.location || '';
    cgEl.value = settings.caregiver || '';
    azaEveryEl.value = settings.azaEvery || '2';
  }
}

// Call on page load
loadSettings();
```

### Adding Export Formats

To export as JSON or CSV:

```javascript
function exportAsJSON() {
  const schedule = {
    startDate: startEl.value,
    endDate: endEl.value,
    medications: []
  };
  
  // Gather data...
  
  const blob = new Blob([JSON.stringify(schedule, null, 2)], 
    { type: 'application/json' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = 'roscoe-schedule.json';
  a.click();
}
```

### Adding Email Integration

For sending schedules via email (requires server):

```javascript
async function emailSchedule() {
  const pdfData = /* capture PDF */;
  
  await fetch('/api/send-email', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      to: cgEl.value,
      subject: 'Roscoe Medication Schedule',
      pdf: pdfData
    })
  });
}
```

## Security Considerations

### User Uploaded Images

- Processed entirely client-side (FileReader API)
- Never sent to a server
- Stored only in memory
- Cleared on page reload

### Data Privacy

- No analytics or tracking
- No external API calls
- No data sent to servers
- All processing done locally

### Safe for Sensitive Information

Yes! The app:
- Runs entirely offline
- Doesn't connect to the internet
- Doesn't save to cloud
- Data stays on your device

## Performance Optimization

### Image Optimization

```javascript
// Add image compression (optional)
function compressImage(file, maxWidth = 800) {
  return new Promise((resolve) => {
    const reader = new FileReader();
    reader.onload = (e) => {
      const img = new Image();
      img.onload = () => {
        const canvas = document.createElement('canvas');
        const ratio = Math.min(maxWidth / img.width, 1);
        canvas.width = img.width * ratio;
        canvas.height = img.height * ratio;
        const ctx = canvas.getContext('2d');
        ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
        resolve(canvas.toDataURL('image/jpeg', 0.8));
      };
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  });
}
```

### Lazy Loading

For very long schedules (30+ days), consider:

```javascript
// Virtual scrolling for 100+ day schedules
// Not implemented by default (not needed for typical use)
```

## API Reference

### Main Functions

```javascript
// Parse date string to Date object
parseDateInput(value: string): Date

// Convert Date to input value string
toLocalInputValue(date: Date): string

// Add days to a date
addDays(date: Date, days: number): Date

// Format date for display
formatDateNice(date: Date): string

// Apply scale transformation
applyScale(percent: number): void

// Build the schedule
build(): boolean

// Show toast notification
showToast(message: string): void
```

---

**Questions or suggestions?** Open an issue or submit a pull request!
