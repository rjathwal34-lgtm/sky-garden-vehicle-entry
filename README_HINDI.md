# Sky Garden Vehicle Entry — Firebase PWA starter (आपके प्रोजेक्ट के लिए configured)

## अभी क्या तैयार है
- `index.html` में आपके Sky Garden Firebase project की Web config जोड़ दी गई है।
- Email/Password login मौजूद है; app में नया account बनाने का विकल्प नहीं है। एक ही Firebase Auth account को सभी मोबाइलों पर इस्तेमाल करें।
- Vehicle records Firestore collection `vehicles` में realtime sync के लिए कोड मौजूद है।
- `firestore.rules` को एक Auth UID तक सीमित रखने के लिए बनाया गया है। Rules publish करने से पहले placeholder को वास्तविक UID से बदलना अनिवार्य है।

## अगला ज़रूरी काम: Firestore Rules सुरक्षित तरीके से सेट करें
1. Chrome में Firebase Console खोलें और अपना project `sky-garden-vehicle-entry-62c8e` खोलें।
2. **Authentication > Users** खोलें और अपने बनाए हुए एकमात्र user पर टैप/क्लिक करें।
3. उस user का **UID** कॉपी करें (यह password नहीं है; इसे निजी लॉगिन जानकारी की तरह सार्वजनिक चैट में साझा न करें)।
4. इस फ़ोल्डर की `firestore.rules` फ़ाइल खोलें और `REPLACE_WITH_YOUR_AUTH_USER_UID` की जगह UID डालें।
5. Firebase Console में **Firestore Database > Rules** खोलें। फ़ाइल की पूरी सामग्री वहाँ पेस्ट करें और **Publish** दबाएँ।
6. जब तक UID सही तरह से नहीं डाला जाता, नियम Publish न करें; इससे डेटा access बंद रह सकता है।

## Hosting / मोबाइल पर चलाना
यह ZIP अपने-आप इंटरनेट पर प्रकाशित नहीं होती। HTML modules, Firebase login, PWA install और multi-device sync के लिए app को HTTPS hosting पर रखना होगा। Android मोबाइल से GitHub Pages जैसे host का उपयोग किया जा सकता है; फिर HTTPS URL को Chrome में खोलकर app install करें। केवल फ़ाइल को File Manager से खोलने पर Firebase module/service worker पूरी तरह काम नहीं कर सकते।

## महत्वपूर्ण
- Firebase Web config ब्राउज़र में दिखने के लिए बनी होती है; यह password या service-account key नहीं है।
- इस app में public sign-up UI नहीं है। अपना एक ही account सभी devices पर उपयोग करें।
- UID-आधारित Firestore Rules के कारण सिर्फ उसी account को shared vehicle records पढ़ने/लिखने/मिटाने की अनुमति मिलेगी।
- पुरानी HTML/localStorage में पहले से मौजूद records अपने-आप cloud में import नहीं होंगे। पुरानी file का backup रखें।
- `manifest.json`, `sw.js`, `icons/` को `index.html` के साथ उसी folder में रखें।
