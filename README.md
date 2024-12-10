
# RandNSFW Bookmarklet

Bookmarklet replacement for the Reddit /r/randnsfw subreddit that has been removed recently. This will randomly open a subreddit from the list stored in the `Subs2024.txt` file.

Credit to Demigod787 for the Subs2024.txt file - https://old.reddit.com/user/Demigod787/overview

## Installation Instructions

### Prerequisites:
- A modern web browser (e.g., Google Chrome, Mozilla Firefox, Microsoft Edge).
- A GitHub account (optional, if you'd like to fork or make changes).

### Steps to Install the Bookmarklet:

1. **Download the `randnsfw_bookmarklet.js` File:**
   - Download the `randnsfw_bookmarklet.js` file from the repository.
   - You can either:
     - **Clone the repository** using Git:
       ```bash
       git clone https://github.com/Tharic99/randnsfw.git
       ```
     - Or **download it directly** as a `.js` file from GitHub:
       - Navigate to the `randnsfw_bookmarklet.js` file in the repository.
       - Click on the "Raw" button and right-click to save the file to your computer.

2. **Create the Bookmarklet in Your Browser:**
   - Open your browser and go to the bookmarks bar.
   - Right-click the bookmarks bar (or open your browser's bookmarks manager).
   - Select **"Add new bookmark"** or **"Add page"**.
   - In the **"Name"** field, enter a name like `RandNSFW Bookmarklet`.
   - In the **"URL"** or **"Location"** field, paste the following code:
     ```javascript
     javascript:(function(){const fileUrl='https://raw.githubusercontent.com/Tharic99/randnsfw/refs/heads/main/Subs2024.txt';fetch(fileUrl).then(response=>{if(!response.ok)throw new Error('Failed to fetch the file.');return response.text();}).then(data=>{alert('File contents:\n'+data);const lines=data.split('\n').map(line=>line.trim());console.log('Lines:',lines);const validLines=lines.filter(line=>/^[0-9]+\|/.test(line));console.log('Valid Lines:',validLines);const subreddits=validLines.map(line=>line.split('|')[1]?.trim()).filter(Boolean);console.log('Extracted Subreddits:',subreddits);if(subreddits.length===0)throw new Error('No valid subreddits found.');const randomSub=subreddits[Math.floor(Math.random()*subreddits.length)];window.open(`https://www.reddit.com/${randomSub}`,'_blank');}).catch(error=>{alert('Error: '+error.message);});})();
     ```

3. **Save the Bookmarklet:**
   - After pasting the above code, click **Save**.
   - The bookmarklet will now appear in your bookmarks bar.

4. **Using the Bookmarklet:**
   - Open any webpage (e.g., your browser’s homepage or any Reddit page).
   - Click the `RandNSFW Bookmarklet` from your bookmarks bar.
   - The bookmarklet will fetch a list of subreddits from the `Subs2024.txt` file hosted on GitHub.
   - It will randomly open a new tab with one of the listed subreddits.

5. **Troubleshooting:**
   - If the bookmarklet doesn’t work, ensure that the file at `https://raw.githubusercontent.com/Tharic99/randnsfw/refs/heads/main/Subs2024.txt` is accessible and correctly formatted.
   - Check your browser console (F12 → Console) for any errors.

---

### Additional Notes:
- **File Updates:** If you update the `Subs2024.txt` file on GitHub, the bookmarklet will automatically reflect the changes.
- **Browser Support:** The bookmarklet should work in modern browsers such as Google Chrome, Firefox, and Microsoft Edge. Make sure your browser allows JavaScript bookmarklets.

