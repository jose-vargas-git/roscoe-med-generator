# 📖 Usage Guide

Complete guide to using the Roscoe Medication Schedule Generator.

## Table of Contents

1. [Opening the App](#opening-the-app)
2. [Generating a Schedule](#generating-a-schedule)
3. [Understanding the Output](#understanding-the-output)
4. [Printing and Sharing](#printing-and-sharing)
5. [Advanced Features](#advanced-features)
6. [Tips and Best Practices](#tips-and-best-practices)

## Opening the App

### On iOS (iPhone/iPad)

**Method 1: Files App**
1. Navigate to the file in Files app
2. Tap `index.html`
3. Select "Safari" or your preferred browser

**Method 2: Add to Home Screen**
1. Open the file in Safari
2. Tap the Share button (square with arrow up)
3. Scroll and tap "Add to Home Screen"
4. Name it "Roscoe Meds"
5. Tap "Add"
6. Now you have a quick-launch icon!

**Method 3: Direct Link**
If hosted on a server, just visit the URL in Safari.

### On Desktop

**Simplest:** Double-click `index.html` in your file explorer

**Alternative:** Serve via HTTP
```bash
# From project root
python3 -m http.server 8000
# Visit: http://localhost:8000/
```

## Generating a Schedule

### Step 1: Click "Generate New Schedule"

The configuration dialog will open with several options.

### Step 2: Set Date Range

**Start Date:**
- The first day you need medication tracking
- Defaults to today's date
- Can be in the past or future

**End Date:**
- The last day of medication tracking
- Must be same day or after start date
- Defaults to 7 days from start

**Example Scenarios:**
- Weekend trip: Fri → Sun (3 days)
- Week-long boarding: Mon → Sun (7 days)
- Extended vacation: Day 1 → Day 14 (14 days)

### Step 3: Add Caregiver Information (Optional)

**Care Location:**
- Where Roscoe will be staying
- Examples: "Happy Paws Boarding", "Friend's House", "Grandma's"
- Appears in the footer of the printout

**Caregiver Name:**
- Who will be administering medications
- Examples: "Sarah Johnson", "Boarding Staff", "Mom"
- Also appears in footer

These fields help identify who the schedule is for, especially useful if you have multiple caregivers.

### Step 4: Add Special Notes (Optional)

**Use this field for:**
- Emergency contact information
- Feeding times and instructions
- Special care instructions
- Vet contact information
- Any allergies or sensitivities
- Behavioral notes

**Example Notes:**
```
Emergency contact: John (555) 123-4567
Feed at 8am and 6pm
Walk 3 times daily
Prefers soft food mixed with dry
Vet: Happy Tails Animal Clinic (555) 999-8888
```

### Step 5: Configure Azathioprine Schedule

**Azathioprine on Start Date:**
- ✅ Checked: Roscoe gets Aza on the first day
- ☐ Unchecked: Roscoe gets Aza on the second day

**Azathioprine Frequency:**
- **Every other day** (most common): Day 1, 3, 5, 7, 9...
- **Every 3 days**: Day 1, 4, 7, 10...
- **Every 4 days**: Day 1, 5, 9, 13...

💡 **Tip:** The app automatically calculates which days to give Azathioprine based on your settings!

### Step 6: Add Header Image (Optional)

**To add a photo of Roscoe:**
1. Click "Choose File"
2. Select a photo from your device
3. Image will appear small at the top of the schedule
4. Best results with square or portrait-oriented photos

**Recommended:**
- File size: Under 5MB
- Formats: JPG, PNG, HEIC (iOS)
- Dimensions: 500x500px or larger

### Step 7: Adjust Print Scale (Optional)

**Default: 80%**

**When to adjust:**
- Schedule too long (doesn't fit page): Decrease scale (60-75%)
- Schedule too small (hard to read): Increase scale (85-120%)
- Lots of days (10+): Lower scale to 70-75%
- Few days (3-5): Can use 90-100%

The scale control at the top also lets you preview the size in real-time!

### Step 8: Build & Print

Click the blue "Build & Print" button:
1. App generates the schedule
2. Loads any image you selected
3. Automatically opens print dialog
4. Review in print preview
5. Save as PDF or print to paper

## Understanding the Output

### Schedule Layout

```
┌─────────────────────────────────────────┐
│  🐕 Roscoe – Medication Checklist       │
├─────────────────────────────────────────┤
│ Date          │ AM           │ PM       │
├───────────────┼──────────────┼──────────┤
│ Mon, Mar 15   │ AM Aza ½ tab │ PM Cose…│
│               │              □          │
├───────────────┼──────────────┼──────────┤
│ Tue, Mar 16   │ AM —         │ PM Cose…│
│               │              □          │
└─────────────────────────────────────────┘
```

### Table Columns

**Date Column:**
- Shows day of week and date
- Format: "Mon, Mar 15"
- Makes it easy to track which day

**AM (Breakfast) Column:**
- Shows morning medication
- Azathioprine ½ tab (on scheduled days)
- "—" means no morning medication that day
- Checkbox to mark when given

**PM (Dinner) Column:**
- Shows evening medication
- Cosequin ½ tab (every day)
- Always has a checkbox

### Checkboxes

The checkboxes are:
- **Interactive** – Can be checked/unchecked
- **Print-friendly** – Appear as empty boxes on printout
- **Touch-optimized** – Large enough for fingers on mobile
- **Purpose** – Caregiver checks them off as medications are given

### Footer Information

**Line 1: Medication Details**
```
Meds: AM – Azathioprine ½ tab (per schedule). 
      PM – Cosequin ½ tab daily with dinner.
```

**Line 2: Metadata (if provided)**
```
Location: Happy Paws Boarding • Caregiver: Sarah Johnson
```

**Line 3: Notes (if provided)**
```
Notes: Emergency contact: (555) 123-4567. Feed at 8am and 6pm.
```

## Printing and Sharing

### Saving as PDF (Recommended)

**iOS:**
1. In print preview, pinch-to-zoom to check layout
2. Tap "Print" in top-right
3. Select "Save to Files"
4. Choose location (iCloud Drive recommended)
5. Tap "Save"

**macOS:**
1. In print dialog, click "PDF" dropdown (bottom-left)
2. Select "Save as PDF"
3. Choose filename and location
4. Click "Save"

**Windows:**
1. In print dialog, select "Microsoft Print to PDF"
2. Click "Print"
3. Choose filename and location
4. Click "Save"

### Sharing Digitally

**From iOS:**
- Files app → Long press PDF → Share
- AirDrop to nearby devices
- Message or Email as attachment
- Upload to iCloud, Dropbox, etc.

**From Desktop:**
- Email as attachment
- Upload to cloud storage
- Share via messaging apps
- Send via secure file transfer

### Printing on Paper

**iOS (with AirPrint):**
1. Follow steps above but select your printer
2. Choose number of copies
3. Tap "Print"

**Desktop:**
1. Select your printer in print dialog
2. Set to portrait orientation
3. Adjust scale if needed (80% recommended)
4. Print

**Print Settings:**
- **Size:** 5" wide (portrait)
- **Color:** Color or B&W both work fine
- **Quality:** Normal is sufficient
- **Margins:** Pre-configured automatically

### What Format to Share?

**PDF (Best for most situations):**
- ✅ Preserves layout exactly
- ✅ Can't be accidentally edited
- ✅ Opens on any device
- ✅ Professional appearance

**Print on Paper (Best for physical posting):**
- ✅ Can post on fridge or wall
- ✅ No device needed to reference
- ✅ Can't lose due to device issues
- ✅ Tangible checklist

**HTML File (Advanced):**
- ✅ Caregivers can generate their own schedules
- ✅ Useful for recurring care situations
- ✅ Can be customized if needed

## Advanced Features

### Real-Time Scale Adjustment

The scale slider at the top lets you preview different sizes:
- Adjust slider between 60% and 120%
- See changes immediately
- Doesn't affect the printed version until you generate again

### Custom Medication Schedules

The app supports multiple Azathioprine frequencies:
- Every 2 days (default)
- Every 3 days
- Every 4 days

This flexibility helps if Roscoe's medication schedule changes.

### Photo Header

Adding Roscoe's photo:
- Makes the schedule more personal
- Helps new caregivers identify him
- Professional touch for boarding facilities
- Optional but recommended!

### Offline Usage

Once loaded, the app works completely offline:
- No internet connection needed
- Save the HTML file to Files app on iOS
- Keep a copy on USB drive
- Works great for remote locations

## Tips and Best Practices

### For First-Time Users

1. **Start simple** – Just set dates and click "Build & Print"
2. **Try the preview** – Use the scale slider to see different sizes
3. **Test print** – Print one copy first to check layout
4. **Add details later** – Start basic, add caregiver info as needed

### For Regular Users

1. **Save as template** – Keep one version for quick reference
2. **Batch create** – Generate multiple schedules for the year
3. **Digital copies** – Save PDFs to iCloud for easy access
4. **Physical backup** – Print an extra copy for emergencies

### For Caregivers

1. **Post prominently** – Fridge, near food, or medication area
2. **Check off immediately** – Don't rely on memory
3. **Double-check dates** – Verify you're looking at current schedule
4. **Mark with pen** – Physical copies can be marked permanently

### For Boarding Facilities

1. **Print at drop-off** – Show caregiver the schedule immediately
2. **Leave two copies** – One for staff, one for Roscoe's file
3. **Include photo** – Helps staff identify correct pet
4. **Clear notes** – Include ALL emergency contacts and instructions

### Medication Administration Tips

1. **Set reminders** – Phone alarms for AM and PM
2. **Consistent times** – Try to give medications at same time daily
3. **With food** – Both medications should be given with meals
4. **Check off right away** – Mark checkbox immediately after giving

### Schedule Duration Guidelines

**Recommended lengths:**
- Weekend: 3-4 days
- Week-long: 7-8 days
- Extended: 10-14 days
- Maximum: Up to 30 days (adjust scale down to 60-70%)

### Storage Recommendations

**Digital Copies:**
- Store in dedicated "Roscoe" folder
- iCloud Drive for iOS users
- Include date in filename: `Roscoe_Schedule_Mar15-22.pdf`
- Keep recent schedules for reference

**Physical Copies:**
- Laminate for reusability (use dry-erase markers for checkboxes)
- Keep in pet care binder
- Post in visible location
- Archive completed schedules for health records

## Common Questions

### Can I edit a generated schedule?

The checkboxes are interactive, but the dates/medications are set when generated. To change, regenerate a new schedule.

### How many days can I schedule?

Technically unlimited, but:
- 7-10 days: Perfect (fits well)
- 14 days: Good (may need to reduce scale)
- 21-30 days: Possible (reduce scale to 60-70%)
- 30+ days: Consider splitting into multiple schedules

### What if I make a mistake?

Simply click "Generate New Schedule" again and create a corrected version. The app doesn't save, so each generation is fresh.

### Can multiple people use this?

Yes! The HTML file can be:
- Shared with anyone
- Used on multiple devices
- Kept by different family members
- Given to regular caregivers for future use

### Does this work offline?

Yes! Once you open the HTML file:
- Works without internet
- All features available
- Can generate unlimited schedules
- Only limitation: Can't sync across devices (it's local)

### Can I customize medications?

Yes, but requires editing the HTML file. See [TECHNICAL.md](TECHNICAL.md) for instructions.

### What if Roscoe's schedule changes?

Simply generate a new schedule with updated settings. The app is flexible and can accommodate changes.

## Troubleshooting

See [TECHNICAL.md](TECHNICAL.md) for technical troubleshooting and customization options.

---

**Need more help?** Check the [README.md](../README.md) or [TECHNICAL.md](TECHNICAL.md) documentation!
