# [Route Groups](https://nextjs.org/docs/app/building-your-application/routing/route-groups)

In the app directory, _nested folders are normally mapped to URL paths_. However, you can mark a folder as a Route Group to prevent the folder from being included in the route's URL path.

This allows you to organize your route segments and project files into logical groups without affecting the URL path structure.

## Convention

A route group can be created by wrapping a folder's name in parenthesis: (folderName)

**Organize routes without affecting the URL path**
To organize routes without affecting the URL, create a group to keep related routes together.

- The folders in parenthesis will be omitted from the URL (e.g. `(marketing)` or `(shop)`).

![image](https://nextjs.org/_next/image?url=%2Fdocs%2Fdark%2Froute-group-organisation.png&w=1920&q=75&dpl=dpl_DEK6Wi8dCdrZ284BPCfVTgu7ynKi)

![image](https://nextjs.org/_next/image?url=%2Fdocs%2Fdark%2Froute-group-opt-in-layouts.png&w=1920&q=75&dpl=dpl_DEK6Wi8dCdrZ284BPCfVTgu7ynKi)

**Good to know:**

- The naming of route groups has no special significance other than for organization. They do not affect the URL path.

- Routes that include a route group should not resolve to the same URL path as other routes. For example, since route groups don't affect URL structure, `(marketing)/about/page.js` and `(shop)/about/page.js` would both resolve to `/about` and **cause an error.**

- If you use multiple root layouts without a top-level layout.js file, your home page.js file should be defined in one of the route groups, For example: `app/(marketing)/page.js`.

- Navigating across multiple root layouts will cause a full page load (as opposed to a client-side navigation). For example, navigating from `/cart` that uses `app/(shop)/layout.js` to `/blog` that uses `app/(marketing)/layout.js` will cause a full page load. This only applies to multiple root layouts.
