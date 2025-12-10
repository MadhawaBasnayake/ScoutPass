# ⚜️ ScoutPass - Digital Command Center

> **Developed by:** Madhawa Basnayake  
> **Version:** 4.0 (Stable)

**ScoutPass** is a complete Event Management System tailored for Scout Camps. It allows you to manage registrations, track attendance via QR codes, and monitor camp security in real-time.

---

## 🛠️ Setup Guide (For Beginners)

If you have zero coding knowledge, don't worry! Follow these 5 steps exactly to get your system running.

### Step 1: Create a Google Firebase Account
1.  Go to [console.firebase.google.com](https://console.firebase.google.com/).
2.  Login with your Gmail account.
3.  Click on the big box that says **"Add project"** (or "Create a project").
4.  Enter a name (e.g., `ScoutPass`) and click **Continue**.
5.  Turn **OFF** "Google Analytics" (you don't need it) and click **Create Project**.
6.  Wait a few seconds and click **Continue**.

### Step 2: Enable Database & Login
Now you are inside your project dashboard.

**A. Enable Login System:**
1.  On the left menu, click **Build** -> **Authentication**.
2.  Click **"Get Started"**.
3.  Under "Sign-in providers", click **Email/Password**.
4.  Turn on the **Enable** switch and click **Save**.

**B. Enable Database:**
1.  On the left menu, click **Build** -> **Realtime Database**.
2.  Click **"Create Database"**.
3.  Choose a location (Singapore or US is fine) -> Click **Next**.
4.  **🔴 VERY IMPORTANT:** Select **"Start in test mode"**.
5.  Click **Enable**.

### Step 3: Get Your Secret Codes (API Keys)
1.  Click the **Gear Icon ⚙️** (Project Settings) at the top-left corner (next to "Project Overview").
2.  Scroll down to the bottom where it says "Your apps".
3.  Click the **</>** icon (which means Web).
4.  Type a name (e.g., `ScoutWeb`) and click **Register app**.
5.  You will see a code block. Look for the part starting with `const firebaseConfig = { ... };`.
6.  **COPY** the text inside the curly brackets `{ ... }`. It looks like this:
    ```javascript
    apiKey: "AIzaSyB...",
    authDomain: "...",
    projectId: "...",
    // copy all these lines
    ```

### Step 4: Connect the Code
1.  Open the 3 files (`index.html`, `dashboard.html`, `scanner.html`) using **Notepad** or a code editor (like VS Code).
2.  Scroll down until you find this line:
    `// 🔴 TODO: PASTE YOUR FIREBASE CONFIG HERE`
3.  Delete the placeholder text and **PASTE** your copied codes from Step 3.
4.  **Save** all 3 files.

### Step 5: Create the First "Admin" (The Tricky Part)
Since the system is empty, you need to manually create the first Boss (Admin) to log in.

1.  Go back to **Firebase Console** -> **Authentication**.
2.  Click **"Add user"**.
3.  Enter an email (e.g., `admin@scout.com`) and a password (e.g., `123456`). Click **Add user**.
4.  Copy the **User UID** (a long code like `7Hk9s...`) next to the user you just created.

Now, give this user "Admin" power:
1.  Go to **Realtime Database** on the left menu.
2.  Hover over the database URL (root) and click the **+ (plus)** button.
3.  In the box named *Name*, type: `users`
4.  Click the **+ (plus)** button next to `users`.
5.  In the *Name* box, paste the **User UID** you copied earlier.
6.  Click the **+ (plus)** button next to the UID.
7.  Add two entries inside this UID:
    * Name: `email` | Value: `admin@scout.com` -> Click Add.
    * Name: `role`  | Value: `admin` -> Click Add.

**It should look like this structure:**
