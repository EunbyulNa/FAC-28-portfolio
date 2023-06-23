## 1. Write code that executes asynchronously

- This function uses fetch to asynchronously retrieve a static map image from a URL. It awaits the completion of the fetch operation before proceeding.

```js
async function fetchStaticMap(lat, lon) {
  try {
    const staticmap = await fetch(`https://maps.geoapify.com/v1/staticmap?style=osm-carto&center=lonlat:${lon},${lat}&zoom=14&marker=lonlat:${lon},${lat};color:%23ff0000;size:medium&apiKey=${ApiKey}`);
    if (!staticmap.ok) throw new Error(staticmap.status);
    const mapUrl = staticmap.url;
    const mapImg = document.querySelector('#mapImg');
    mapImg.src = mapUrl;
  } catch (error) {
    handleError("Sorry, we cannot update the map.");
  }
}
```

- This function uses fetch to asynchronously retrieve sunrise and sunset information from an API. It awaits the completion of the fetch operation before proceeding.

```js
async function fetchSunriseSunset(lat, lon) {
  try {
    const sunApiToday = await fetch(`https://api.sunrisesunset.io/json?lat=${lat}&lng=${lon}`);
    if (!sunApiToday.ok) throw new Error(sunApiToday.status);
    const today = await sunApiToday.json();
    displaySunriseSunset(lat, lon, today);
  } catch (error) {
    handleError("Sorry, we cannot update sunrise-sunset.");
  }
}
```


## 2. Use callbacks to access values that aren’t available synchronously
- I didn't use callback functions. Instead, I use the async/await syntax to handle asynchronous operations. In my code, I made use of `async` keyword before certain functions and used `await` keyword to pause the execution and wait for promises to resolve. By doing so, I was able to achieve the desired asynchronous behavior without explicitly passing callbacks.

## 3. Use promises to access values that aren’t available synchronously
- I did not explicitly create promises using the Promise constructor. Instead, I used the async/await syntax, which is built on top of promises.
  In the `fetchStaticMap`, `fetchSunriseSunset`, and `fetchMonthlyAverage` functions use `fetch` method, which returns a promise. By marking these functions as 
 `async` and using the `await` keyword before the `fetch` calls, it's effectively awaiting the resolution of the promises returned by the fetch function.
  The await keyword allows me to pause the execution of an `async` function until the `promise` is `resolved` or `rejected.` It simplifies the syntax and makes 
 the code look more synchronous, while still utilizing `promises` under the hood.

## 4. Use the fetch method to make HTTP requests and receive responses
```js
async function fetchStaticMap(lat, lon) {
  try {
    const staticmap = await fetch(`https://maps.geoapify.com/v1/staticmap?style=osm-carto&center=lonlat:${lon},${lat}&zoom=14&marker=lonlat:${lon},${lat};color:%23ff0000;size:medium&apiKey=${ApiKey}`);
    if (!staticmap.ok) throw new Error(staticmap.status);
    const mapUrl = staticmap.url;
    const mapImg = document.querySelector('#mapImg');
    mapImg.src = mapUrl;
  } catch (error) {
    handleError("Sorry, we cannot update the map.");
  }
}
```
- In this code, I use the `fetch` method to make an HTTP request to the Sunrise-Sunset API. The response from the API depends on the user's input, specifically the latitude and longitude values.
After making the request with fetch, I checked the status property of the sunApiToday response. If the status is not equal to ok, I throw an error to indicate that there was a problem with the request. Otherwise, I proceed to retrieve the desired result from the response.

## 5. Configure the options argument of the fetch method to make GET and POST requests

## 6. Use the map array method to create a new array containing new values
```js
  try {
    // Graph API fetch
    const labels = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'June', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
    const data = monthlyAverages.map((data) => data.average);
    const graphApi = `https://quickchart.io/chart?c={type:'bar',data:{labels:${JSON.stringify(labels)},datasets:[{label:'Average Hours',data:[${data}]}]}}`;
    const graph = await fetch(graphApi);
    if (!graph.ok) throw new Error(graph.status);
    const graphImg = document.querySelector('#graphImg');
    graphImg.src = graph.url;
  } catch (error) {
    handleError("Sorry, we cannot update the monthly average daylight graph.");
  }
}
```
- `fetchMonthlyAverage` function retrieves data for each month of the year and calculates the average value for each month based on the fetched data. The `monthlyAverages` array stores objects containing the `month` and its corresponding `average` value.
To generate a graph, I use `map` array method. It extracts the `average` values from each object in the `monthlyAverages` array and creates a new array called `data` containing only the average values. This new array is then used to generate the graph.
  
## 7. Use the filter array method to create a new array with certain values removed
- In this project, I didn't use `filter` method.

## 8. Access DOM nodes using a variety of selectors

```js
// selects the element with the class ".sunset-times".
const dataText = document.querySelector('.sunset-times');
// selects the element with the class ".you-are-here".
const youAreHere = document.querySelector('.you-are-here');
// selects the element with the class ".current-time".
const currentTime = document.querySelector('.current-time');
// selects the element with the class ".bar-container".
const barContainer = document.querySelector('.bar-container');
```

## 9. Add and remove DOM nodes to change the content on the page

## 10. Toggle the classes applied to DOM nodes to change their CSS properties

## 11. Use consistent layout and spacing

## 12. Follow a spacing guideline to give our app a consistent feel

## 13. Debug client side JS in our web browser

## 14. Use console.log() to help us debug our code
