---
date created: Thursday, February 5th 2026, 3:08:51 pm
date modified: Saturday, February 7th 2026, 4:03:53 pm
---

# Project Setup:

Start by either downloading or copying the `TMA02_v1` project files. We can do this in the terminal via the following command:

```Bash
cp -r ~/block_2/skeletons/tma02 ~/block_2/work/
cd /home/ou/TM352-25J/block_2/work/tma02_v1 # Navigate to the new folder.
```

Then we can use `npm run` to see what actions we can run via the node package manager. This is a smart thing to check, when you are starting a new project from someone else.

```Bash
npm run 

...SNIP...
Lifecycle scripts included in tma02-documentation@1.0.0:
  test
    cd reactnative && npx jest
available via `npm run-script`:
  build
    cd reactnative && npm run build-docs && cd .. && cd api && npm run build-docs && cd .. && node scripts/build-docs-simple.js
  serve
    npm run build && npx http-server docs-html -p 8080 -o
  clean
    rimraf docs-html
  install-deps
    npm ci && cd reactnative && npm ci && cd .. && cd api && npm ci
  reactnative:dev
    cd reactnative && npm run auto
  service:dev
    cd api && npm run dev
  dev
    concurrently "npm run service:dev" "npm run reactnative:dev"
  assess
    npm run install-deps && cd reactnative && npm run test
...SNIP...

```

What we care about here is doing the following:

1. Installing the necessary dependencies first. `npm run install-deps`
	1. This runs our `ci` command on all the areas we care about, ensuring that everything is up to date and functioning well.
		1. This clean install ensures that our environment will match production or a teammate, compared to `npm install`.
2. We then want to start our development server and api. This is done via `npm run dev`
	1. Make sure when you are developing, that you go into DevTools > pick a smartphone display.
3. When we want to check the work, we would run `npm run assess`, this will give us our mark.
	1. We then need to screenshot this for the submission.

We can look at the API documentation be doing the following:
1. Navigate to the `api` folder. (`cd /work/tma02_v1/api`)
2. `npm run dev` - navigate to the API link and access the documentation.

We can also look at more documentation by running the `npm run serve` command as well.
***

When picking QR code, I decided to go with the react-fancy-qrcode for a few reasons:

1. It was recommended in the testing suite as a potential option
2. `react-fancy-qrcode` has lower dependencies, peer dependencies, and development dependencies than the `react-native-qrcode-svg`
	1. Dependencies 2 VS 3
	2. Peer Dependencies 1 VS 3
	3. Development Dependencies 5 VS 10
3. This means that there is fewer setup and configuration which needs to be done, it also ensures that the build process is simpler and has less future version conflicts.
4. It is also smaller (38.56kB VS 958.34kB), this results in a smaller bundle size and less code to maintain or worry about.
	1. This is particularly beneficial if the application scales to handle more features.
	   
	   
**Application to scenario** (worth up to 14 marks) — your current draft lists generic facts. You need to tie each point to _your specific project_. For example:

- "Since the app runs via `npm run dev` in the browser, web rendering support is essential — `react-fancy-qrcode` handles this natively while `react-native-qrcode-svg` requires additional `react-native-svg` configuration for web"
- "The QR code displays the `ticket.id` for seat verification at the amphitheatre, so the library only needs basic string-to-QR functionality — `react-fancy-qrcode`'s simpler API is sufficient"

**Other comparison points you could add:**

- **Maintenance/currency** — when was each library last updated? Check npm for last publish dates
- **Documentation quality** — does one have better docs/examples than the other?
- **Community/issues** — check GitHub issues. Are bugs being fixed? Are there unresolved problems?
- **Platform support** — does each library explicitly support web? This is critical for your setup
- **Licensing** — are both MIT or similar permissive licenses?

**Citations** (up to 4 marks) — you get 1 mark per relevant citation. Cite:

- The npm pages for both libraries
- Your own code where you implement it
- Any React Native documentation you reference
- The course materials if they discuss library evaluation criteria
  
***