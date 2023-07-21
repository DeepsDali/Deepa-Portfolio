# HTTP portfolio

**Aim:** Learn how to manage asynchronous tasks and send HTTP requests using JavaScript.

**Project:** TD Weather App uses postcode to generate a map and accurate sunrise-sunset timings, as well as a comprehensive daily and 5-day weather forecast. To gather this information, the app integrates three APIs: open-meteo.com, postcodes.io, and thunderforest.com.

https://github.com/DeepsDali/Weather-Forecast-Project/deployments/activity_log?environment=github-pages

# Learnings

## 1. Write code that executes asynchronously

The asynchronous code given below is used in the website to return latitude and longitude for a given postcode.

```
export const getLongLat = async (postcode) => {
try {
const postcodeApiUrl = `https://api.postcodes.io/postcodes/${postcode}`;
const response = await fetch(postcodeApiUrl);

    if (response.ok) {
      const data = await response.json();
      const { latitude, longitude } = data.result;
      return { latitude, longitude };
    } else {
      throw new Error(response.status);
    }

} catch (error) {
if (error.message === "404") {
console.error(`⚠️ Couldn't find "${postcode}"`);
throw new NotFoundError();
} else {
console.error("⚠️ Something went wrong");
throw new Error("Failed to fetch latitude and longitude");
}
}
};
```

## 2. Use callbacks to access values that aren’t available synchronously

Used the async/await syntax instead of callbacks.

## 3. Use promises to access values that aren’t available synchronously

Used the async/await syntax instead of callbacks.

## 4. Use the fetch method to make HTTP requests and receive responses

Used fetch method to get admin district.

```
export const getLocation = async (postcode) => {
  try {
    const postcodeApiUrl = `https://api.postcodes.io/postcodes/${postcode}`;
    const response = await fetch(postcodeApiUrl);

    if (response.ok) {
      const data = await response.json();
      const { admin_district } = data.result;
      return { admin_district };
    } else {
      throw new Error(response.status);
    }
  } catch (error) {
    if (error.message === "404") {
      console.error(`⚠️ Couldn't find "${postcode}"`);
      throw new NotFoundError();
    } else {
      console.error("⚠️ Something went wrong");
      throw new Error("Failed to location");
    }
  }
};
```

## 5. Configure the options argument of the fetch method to make GET and POST requests

Used fetch method to make GET requests to different APIs and retrieve data.

## 6. Use the map array method to create a new array containing new values

In this project, map method was not used.

## 7. Use the filter array method to create a new array with certain values removed

In this project, filter method was not used.

## 8. Access DOM nodes using a variety of selectors

```
  const form = document.querySelector("form");
  const output = document.querySelector("#post-code");
  const county = document.querySelector("#county");
  const current = document.querySelector("#current");
  const currentsun = document.querySelector("#currentsun");
  const currSunrise = document.querySelector("#current-sunrise");
  const currSunset = document.querySelector("#current-sunset");
  const forecastMessage = document.querySelector(".forecast-message");
  const invalidMessage = document.querySelector(".invalid-message");
  const mapDiv = document.querySelector("#location");
```

## 9. Add and remove DOM nodes to change the content on the page

Added map of searched postcode.

```
const newImage = createElement("img", {
          src: `${imageURL}`,
          className: "map-image",
          alt: "map of searched postcode",
        });

        if (image) {
          mapDiv.removeChild(image);
        }

        image = newImage;
        mapDiv.appendChild(newImage);

```

## 10. Toggle the classes applied to DOM nodes to change their CSS properties

In this project, toggle was not used with classes.

## 11. Use consistent layout and spacing

The whole site is inside a grid container with header, main and footer sections. The main section is further divided in sub sections in a grid layout

```
.grid-container {
  display: grid;
  grid-template-areas:
    "header "
    "main  "
    "footer";
  gap: 5px;
  min-height: 100vh;
  width: 100%;
}
main {
  display: grid;
  grid-template-areas:
    "inputgrid inputgrid"
    "placegrid placegrid"
    "tempnowgrid sungrid"
    "tempnowgrid sungrid"
    "foregrid foregrid"
    "mapgrid mapgrid";
  gap: 30px;
  max-width: 100vw;
  min-height: 80vh;
  padding: 0 10px;
  justify-content: center;
  align-items: center;
}
```

## 12. Follow a spacing guideline to give our app a consistent feel

The use of CSS Grid throughout the styles provides consistent layouts for different sections and the gap property ensures consistent spacing between grid items.

Padding and margins are used with specific values to create consistent spacing between elements, ensuring an organized and harmonious design.

The use of media queries helps to maintain consistent spacing on different screen sizes. Different styles and spacing are applied based on the screen width to ensure a visually appealing layout on both desktop and mobile devices.

The clamp() function is used in font sizes to ensure that text scales appropriately and consistently based on the screen size. This helps maintain a readable and well-proportioned layout across different devices.

## 13. Debug client side JS in our web browser

Used console.log() or console.error() to log validation-related messages and inspect the DOM elements and their attributes using the browser's Elements tab in the developer tools.

Tested the form with different input values and check if the validation logic is working as expected. Inspect the console for any error messages.

## 14. Use console.log() to help us debug our code

Used Console.log() on event listeners to check if button clicks. Also used for form validation function to check if an input field is empty and on functions dynamically adding elements to the DOM.
