# GOOGLE SHEETS INTEGRATION SETUP GUIDE
# For Lakme Salon Customer Tracker

## WHAT YOU NEED:
- Google account
- 10 minutes of time
- The two files I've provided

## STEP-BY-STEP INSTRUCTIONS:

### STEP 1: CREATE GOOGLE SHEET
1. Go to https://sheets.google.com
2. Click "+ Blank" to create a new spreadsheet
3. Name it "Lakmē Salon Customer Data"
4. In Row 1, add these headers (exactly as written):
   - A1: Timestamp
   - B1: Name
   - C1: Contact
   - D1: Gender
   - E1: Source
   - F1: Type
   - G1: Entry Type
   - H1: Payment Method
   - I1: Services/Query
   - J1: Amount
   - K1: Locality

### STEP 2: OPEN APPS SCRIPT EDITOR
1. In your Google Sheet, click "Extensions" menu (top bar)
2. Click "Apps Script"
3. A new tab will open with a code editor
4. You'll see a blank function called "myFunction" - DELETE ALL OF IT

### STEP 3: PASTE THE SCRIPT
1. Open the file "google-apps-script.js" I provided
2. Copy ALL the code from that file
3. Paste it into the Apps Script editor (replacing everything)
4. Click the "Save" icon (💾) or press Ctrl+S
5. Name your project "Salon Tracker API" (or any name you want)

### STEP 4: DEPLOY AS WEB APP
1. Click "Deploy" button (top right)
2. Select "New deployment"
3. Click the gear icon ⚙️ next to "Select type"
4. Choose "Web app"
5. Fill in these settings:
   - Description: "Salon Customer API"
   - Execute as: "Me"
   - Who has access: "Anyone" ⚠️ IMPORTANT
6. Click "Deploy"
7. Google will ask for permissions - Click "Authorize access"
8. Choose your Google account
9. Click "Advanced" (if you see a warning)
10. Click "Go to Salon Tracker API (unsafe)" - Don't worry, it's YOUR script
11. Click "Allow"

### STEP 5: COPY THE WEB APP URL
1. After deployment, you'll see a "Web app URL"
2. It looks like: https://script.google.com/macros/s/AKfycby.../exec
3. Click "Copy" to copy this URL
4. SAVE THIS URL - you need it for the next step!

### STEP 6: UPDATE THE HTML FILE
1. Open the file "index.html" in a text editor (Notepad, VS Code, etc.)
2. Find this line near the top (around line 10-15 in the <script> section):
   
   const GOOGLE_SHEETS_URL = 'PASTE_YOUR_WEB_APP_URL_HERE';
   
3. Replace 'PASTE_YOUR_WEB_APP_URL_HERE' with your actual URL:
   
   const GOOGLE_SHEETS_URL = 'https://script.google.com/macros/s/AKfycby.../exec';
   
4. Save the file

### STEP 7: TEST IT!
1. Open the updated HTML file in your browser
2. Fill in a test customer entry (including Gender and Locality)
3. Click "Add Customer Entry"
4. Go back to your Google Sheet
5. You should see a new row with the customer data!

### STEP 8: DEPLOY TO WEB (Optional)
- Upload the updated HTML file to Netlify/GitHub Pages (as discussed earlier)
- Now anyone opening the URL will save data to YOUR Google Sheet

---

## TROUBLESHOOTING:

### "Not synced to Google Sheets" in console
- Check: Did you paste the correct Web App URL?
- Check: Did you set "Who has access" to "Anyone"?
- Check: Is ENABLE_GOOGLE_SHEETS set to true in the HTML?

### "Authorization required" error
- You need to authorize the script (see Step 4)
- Make sure you clicked "Allow" for all permissions

### Data not appearing in Sheet
- Check: Are the column headers exactly as specified in Step 1?
- Try: Redeploy the Apps Script (Deploy → Manage Deployments → New Version)

### Can't find "Extensions" menu
- You might be in old Google Sheets
- Click "Tools" → "Script editor" instead

---

## IMPORTANT NOTES:

✅ Data is saved in BOTH places:
   - Local browser (localStorage)
   - Google Sheets (cloud backup)

✅ If Google Sheets fails, data still saves locally

✅ You can export CSV anytime as additional backup

✅ The Web App URL is public but doesn't expose your sheet data
   - Only allows adding rows, not reading/deleting

✅ To stop syncing temporarily:
   - Set ENABLE_GOOGLE_SHEETS = false in the HTML file

---

## NEW FIELDS ADDED:

📌 **Gender** (Required):
   - Radio buttons: Male, Female, Other
   - Appears after Contact Number

📌 **Locality** (Optional):
   - Text input field
   - Appears at the very end of the form

📌 **Payment Method** (Updated):
   - Added "Coupon" option
   - Options: Cash, Other, Coupon

---

## NEED HELP?
If you get stuck, send me:
1. Screenshot of the error
2. Your Web App URL (I can test it)
3. Which step you're stuck on
