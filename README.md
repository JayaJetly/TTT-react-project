# TTT-react-project
** I have made two components i.e. app.js and fetch.js**

**fetch.js:**

This file consists of two functions: `fetchContent` and `parseContent`. Let's explore the purpose of each function:

1. `fetchContent`: This function is responsible for retrieving the content from the specified URL. It uses the built-in JavaScript `fetch` function to send a GET request and obtain the response. The response is then converted to a text format using the `.text()` method. Ultimately, the function returns the content as a string.

2. `parseContent`: This function accepts the content as input and performs the necessary operations to parse the content and generate a histogram. Here's a breakdown of the steps involved:

   - The content string is split into an array of words using the regular expression `/\s+/`, which matches one or more whitespace characters.
   - An empty object called `wordFrequency` is initialized to store the frequency of each word.
   - For each word in the `words` array, its frequency is incremented and stored in the `wordFrequency` object.
   - The `wordFrequency` object is converted to an array of key-value pairs using `Object.keys` and `Array.prototype.map`. Each key-value pair represents a word and its frequency.
   - The array is sorted in descending order based on the frequency using the `sort` function and a custom comparison function.
   - The top 20 words with the highest frequency are selected using `slice`.
   - The selected words and their frequencies are transformed into an array of objects with `word` and `frequency` properties.
   - Finally, the function returns the resulting array, which represents the histogram data.

**App.js:**

This file contains the primary React component for the application. 

1. The `useState` hook is utilized to manage state within functional components. Two state variables, `histogramData` and `isLoading`, are defined. The `histogramData` state variable stores the histogram data, while `isLoading` indicates whether the data is currently being loaded.

2. The `fetchData` function is an asynchronous function that executes when the Submit button is clicked. It sets the `isLoading` state variable to `true` to indicate that the data is being loaded. Subsequently, it calls the `fetchContent` function from `fetch.js` to retrieve the content from the specified URL. Once the content is obtained, the `parseContent` function is called to extract the histogram data. Finally, the `histogramData` state variable is updated with the parsed data, and `isLoading` is set back to `false`.

3. The `handleExport` function is triggered when the Export button is clicked. It prepares the histogram data in CSV format by creating a string with the word and frequency values. Afterwards, a temporary anchor element is created, where the CSV file is assigned to the `href` attribute, and the file name is specified as the `download` attribute. A simulated click event is then triggered on the element, initiating the download of the CSV file.

4. Within the return statement, the JSX code defines the component's user interface structure. It renders a `div` containing a Submit button, which calls the `fetchData` function upon clicking. If the `histogramData` state variable contains data, a `BarChart` component from the 'recharts' library is rendered. The `BarChart` component utilizes the `histogramData` as the `data` prop to display a bar chart based on the provided data. Additionally, an Export button is rendered, which invokes the `handleExport` function upon clicking.

Above is the explanation for two of the components.
