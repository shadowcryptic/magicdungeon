# Dungeon Horde Table

Run the D&D Dungeon Horde (from hordemagic.com) from your phone while a second screen shows the Horde's battlefield with real card images from Scryfall.

Files:

- `index.html` – the whole app (display and phone controller)
- `config.js` – your Firebase settings (you fill this in)
- `database.rules.json` – security rules to paste into Firebase

Setup takes about 15 minutes, once. Everything used here is free.

---

## 1. Create the Firebase database

1. Go to https://console.firebase.google.com and sign in with a Google account.
2. Click **Create a project**. Name it something like `dungeon-horde`. You can turn off Google Analytics.
3. In the left menu, open **Build > Realtime Database** and click **Create Database**.
   - Location: **Singapore (asia-southeast1)** is closest to Australia.
   - Security rules: choose **Start in locked mode**.
4. Open the **Rules** tab, delete what's there, paste the contents of `database.rules.json`, and click **Publish**.

## 2. Get your web app settings

1. Click the gear icon next to **Project Overview** and choose **Project settings**.
2. Under **Your apps**, click the **Web** icon (`</>`). Give it a nickname (e.g. `table`). Leave "Firebase Hosting" unticked and click **Register app**.
3. You'll see a block of code containing `const firebaseConfig = { ... }`. Copy the values into `config.js`:

```js
window.FIREBASE_CONFIG = {
  apiKey: "AIza...",
  authDomain: "dungeon-horde-xxxx.firebaseapp.com",
  databaseURL: "https://dungeon-horde-xxxx-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId: "dungeon-horde-xxxx",
  appId: "1:1234:web:abcd"
};
```

If `databaseURL` is missing from that block, copy it from the top of the **Realtime Database > Data** page.

## 3. Put it on GitHub Pages

1. On https://github.com click **New repository**. Name it e.g. `dungeon-horde` and make it **Public** (free accounts need a public repo for Pages).
2. Click **uploading an existing file** and drag in `index.html` and `config.js`. Click **Commit changes**.
3. Go to **Settings > Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, Branch to **main** and folder **/ (root)**, then **Save**.
4. After a minute or two the page shows your site address, like `https://yourname.github.io/dungeon-horde/`.

## 4. Play

1. Open your site on the computer driving the second screen and click **Create a table**. It opens the Table Display with a table code and a QR code.
2. Scan the QR code with your phone. It opens the Horde Controller for that table.
3. Choose the number of players and the starting level on your phone and tap **Begin the descent**.

The table code stays in the address, so bookmark both pages to reuse the same table. Make a new table any time from the home page.

---

## Notes

- **Card images** load from Scryfall in each browser when the page opens and are cached on that device for two weeks. Use **Setup > Reload card images and data from Scryfall** to refresh. Cards Scryfall can't find by name show a styled text card instead.
- **Rarity and P/T** also come from Scryfall, so wave endings and attack totals use real card data. You can still override both in the controller.
- **Testing without Firebase:** open `index.html` straight from your computer with an empty `config.js`. It runs on one device and syncs between two browser tabs.
- **Privacy:** anyone who knows a table code can open that table. Codes are random, so this is fine for home games. Don't put anything private in the game.
- **Changing the app later:** edit `index.html` in the GitHub repo (pencil icon) and commit. Pages updates within a minute or two.

Card images and data from Scryfall. Card images © Wizards of the Coast. Unofficial Fan Content permitted under the Wizards of the Coast Fan Content Policy; not approved or endorsed by Wizards.
