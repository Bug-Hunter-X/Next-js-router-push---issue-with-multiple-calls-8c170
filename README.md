# Next.js router.push() Issue

This repository demonstrates a potential issue with Next.js's `router.push()` method when multiple navigation calls are made in rapid succession.  The issue is that if you call `router.push` twice without waiting for the first transition to complete, only the second transition might take effect.

## Steps to Reproduce

1. Clone the repository.
2. Run `npm install` to install dependencies.
3. Run `npm run dev` to start the development server.
4. Navigate to the `/about` page.
5. Click the "Go to Home and then Contact" button.

**Expected behavior:** The application should navigate to the `/` page and then to the `/contact` page. Note that in this example, there is no `/contact` page. This bug will affect any situation that tries to call `router.push()` in succession without awaiting completion. 

**Actual behavior:** Only the navigation to the `/contact` page (or the second call) will occur. The navigation to the `/` page is skipped.

## Possible Solution

The solution involves ensuring that the second navigation call happens only after the first one is complete. This can be done using promises or async/await as explained in the `about.js` file. 
