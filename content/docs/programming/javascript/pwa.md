---
title: "渐进式加载"
weight: 10
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Manifests.json

Manifests.json
```json
{
  "name": "My PWA!",  
  "short_name": "PWA", 
  "start_url": ".",
  "display": "standalone"
}

// name -- PWA name
// short_name -- Show underneath the mobile app icon
// start_url -- If the user taps on the icon, this url is launched
// display -- Customize what browser UI is shown when your app is launched.

```

```html
<link rel="manifest" href="/manifest.json">

```

## Service Worker

service-worker.js
```js
// check if the serviceWorker object exists in the navigator object
if ('serviceWorker' in navigator) {

  // attach event listener  on page l aod
  window.addEventListener('load', function() {

    // register serviceWorker withthe [service-worker.js] file
    navigator.serviceWorker.register('/service-worker.js').then(registration => {

      // Registration was successful
      console.log('ServiceWorker registration successful with scope: ', registration.scope);

    }, function(err) {
      // registration failed :(
      console.log('ServiceWorker registration failed: ', err);
    });

  });
}
// install event for the service worker
self.addEventListener('install', e => {

  e.waitUntil(
    caches.open('site-static').then(cache => {
      cache.addAll(['/', '/index.html'])
    })
  )

})
self.addEventListener('fetch', e => {
  console.log(caches)
  e.respondWith(
    caches.match(e.request).then(res => {
      return res
    })
  )
})

```

Service Worker 基于 promise 语法，这意味着它们默认是异步的。


