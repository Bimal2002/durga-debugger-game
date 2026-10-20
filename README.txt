DURGA DEBUGGER  -  deploy & mobile-app guide  (by bimal.os)
================================================================

WHAT'S IN THIS FOLDER
  index.html             the full game (self-contained)
  manifest.webmanifest   makes it installable as an app
  sw.js                  service worker -> works offline after first load
  icon-192 / 512 / 1024  app icons (gold trishul)

----------------------------------------------------------------
1) DEPLOY THE CODE  (pick any one - all free)
----------------------------------------------------------------
  * GitHub Pages:  push this folder to a repo -> Settings > Pages >
    deploy from branch (root).  URL: https://<user>.github.io/<repo>/
  * Netlify / Vercel:  drag-and-drop this folder at app.netlify.com/drop
    (instant https URL).
  * Cloudflare Pages:  connect the repo or upload the folder.
  Any static host works - it's just files, no backend.

  NOTE: open it over http(s), not file:// , so the service worker and
  "Add to Home Screen" install work.

----------------------------------------------------------------
2) INSTALL AS A MOBILE APP  (PWA - no store needed)
----------------------------------------------------------------
  Once it's on an https URL, on a phone:
   Android (Chrome):  open the URL -> menu -> "Add to Home screen" /
                      "Install app".  Launches fullscreen like a native app.
   iPhone (Safari):   Share -> "Add to Home Screen".
  Works offline after the first open.

----------------------------------------------------------------
3) GET A REAL .APK / .AAB  (for the Play Store or sideloading)
----------------------------------------------------------------
  Easiest - PWABuilder (free, by Microsoft):
   1. Deploy to an https URL (step 1).
   2. Go to https://www.pwabuilder.com and paste that URL.
   3. Click "Package for stores" -> Android -> Download.
      You get a signed .apk (test/sideload) and .aab (Play Store upload).

  Or with Bubblewrap (Google's CLI):
   npm i -g @bubblewrap/cli
   bubblewrap init --manifest https://<your-url>/manifest.webmanifest
   bubblewrap build        # produces app-release-signed.apk

  A true signed APK must be built against the Android SDK on your own
  machine (or PWABuilder's cloud) and signed with your key - that can't be
  faked here, so these are the genuine routes.
