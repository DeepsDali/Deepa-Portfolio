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

Used use the async/await syntax instead of callbacks.

## 3. Use promises to access values that aren’t available synchronously

Used use the async/await syntax instead of callbacks.

## 4. Use the fetch method to make HTTP requests and receive responses

Used fetch method to get admin district

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

## 6. Use the map array method to create a new array containing new values

## 7. Use the filter array method to create a new array with certain values removed

## 8. Access DOM nodes using a variety of selectors

## 9. Add and remove DOM nodes to change the content on the page

## 10. Toggle the classes applied to DOM nodes to change their CSS properties

## 11. Use consistent layout and spacing

## 12. Follow a spacing guideline to give our app a consistent feel

## 13. Debug client side JS in our web browser

## 14. Use console.log() to help us debug our code
