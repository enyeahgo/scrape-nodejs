# scrape-nodejs
```
// npm i puppeteer
const puppeteer = require("puppeteer");

// we're using async/await - so we need an async function, that we can run
const run = async () => {
  // open the browser and prepare a page
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  // open the page to scrape
  await page.goto("https://codesnacks.net");

  // execute the JS in the context of the page to get all the links
  const links = await page.evaluate(() => 
    // let's just get all links and create an array from the resulting NodeList
     Array.from(document.querySelectorAll("a")).map(anchor => [anchor.href, anchor.textContent])
  );

  // output all the links
  console.log(links);

  // close the browser 
  await browser.close();
};

// run the async function
run();
```
