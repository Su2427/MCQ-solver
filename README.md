# Exam Coach – build the APK
Needs Node 18+, JDK 17, Android Studio (SDK).
```
npm init -y
npm i @capacitor/core @capacitor/cli @capacitor/android
npx cap init ExamCoach com.sunil.examcoach --web-dir=www
mkdir www && cp index.html manifest.json sw.js icon.svg www/
npx cap add android && npx cap sync
cd android && ./gradlew assembleDebug
```
APK: `android/app/build/outputs/apk/debug/app-debug.apk` (copy to phone, allow "install unknown apps").
Alternative (no Android Studio): host the folder on HTTPS (GitHub Pages) and generate an APK at pwabuilder.com.
Offline use: libraries load from CDN (internet needed on first use of PDF/OCR). To bundle them, `npm i pdfjs-dist tesseract.js` and copy the files into www/, then change the <script> tags.
Optional: paste an Anthropic API key in the app for AI explanations and AI-made options (stored only on your device).
