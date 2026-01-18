# How to Build APK Files

Each game is set up as a Progressive Web App (PWA) that can be converted to an Android APK. Here are the easiest methods:

---

## Method 1: PWA Builder (Easiest - Recommended)

PWA Builder is a free Microsoft tool that converts PWAs to APKs.

### Steps:

1. **Host the game files** (choose one option):
   - **GitHub Pages**: Push to GitHub, enable Pages in Settings
   - **Netlify**: Drag & drop the game folder at [netlify.com/drop](https://app.netlify.com/drop)
   - **Vercel**: Deploy at [vercel.com](https://vercel.com)

2. **Go to PWA Builder**:
   - Visit [pwabuilder.com](https://www.pwabuilder.com/)
   - Enter your hosted game URL (e.g., `https://yourusername.github.io/games/color-clash/`)
   - Click "Start"

3. **Generate APK**:
   - Click "Package for stores"
   - Select "Android"
   - Choose "APK" format
   - Download the APK file

4. **Install on your phone**:
   - Transfer APK to your phone
   - Enable "Install from unknown sources" in Settings
   - Open the APK to install

---

## Method 2: Bubblewrap CLI (More Control)

Google's official tool for converting PWAs to Android apps.

### Prerequisites:
- Node.js 14+
- Java JDK 8+
- Android SDK

### Steps:

```bash
# Install Bubblewrap
npm install -g @anthropic/anthropic-sdk

# Initialize project (run in game folder)
cd color-clash
bubblewrap init --manifest https://your-hosted-url/manifest.json

# Build APK
bubblewrap build
```

---

## Method 3: WebView Wrapper (Simple Android Studio)

If you have Android Studio installed:

1. Create new Android project
2. Add a WebView to your layout
3. Load the game HTML from assets
4. Build APK

### Quick WebView code:

```kotlin
// MainActivity.kt
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val webView = WebView(this)
        webView.settings.javaScriptEnabled = true
        webView.settings.domStorageEnabled = true
        webView.loadUrl("file:///android_asset/index.html")

        setContentView(webView)
    }
}
```

---

## Method 4: Online APK Builders

Several online services can wrap your HTML games:

1. **WebIntoApp** - [webintoapp.com](https://webintoapp.com)
2. **AppsGeyser** - [appsgeyser.com](https://appsgeyser.com)
3. **GoNative** - [gonative.io](https://gonative.io)

Just upload your HTML files or provide a URL!

---

## Quick Deploy to GitHub Pages

To host your games on GitHub Pages for free:

```bash
# From the games folder
git add .
git commit -m "Add PWA files for APK conversion"
git push

# Then go to GitHub repo Settings > Pages
# Select "main" branch and save
# Your games will be at:
# https://yourusername.github.io/games/color-clash/
# https://yourusername.github.io/games/memory-rhythm/
# etc.
```

---

## Game URLs After Hosting

Once hosted, each game will have its own URL:
- Color Clash: `https://[your-domain]/color-clash/`
- Memory Rhythm: `https://[your-domain]/memory-rhythm/`
- Gravity Flip: `https://[your-domain]/gravity-flip/`
- Orbit Defense: `https://[your-domain]/orbit-defense/`
- Word Snake: `https://[your-domain]/word-snake/`

Use these URLs with PWA Builder to create APKs for each game!

---

## Troubleshooting

**APK won't install?**
- Enable "Install unknown apps" in phone Settings > Security

**Game doesn't work offline?**
- Make sure service worker is registered
- Clear browser/app cache and reload

**Icons not showing?**
- Some tools need PNG icons instead of SVG
- Use an online converter to convert SVG to PNG
