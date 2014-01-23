Because of the way Chromium (or Chromium-based browser) works.

When you try to save an image on a web page using the contextual menu, Chromium will make a request of type `other` (not `image`), so if you disallowed `other` in the *HTTP Switchboard* matrix, the request will be blocked.

Just allow `other` for the hostname corresponding to where the image you want to save is located.
