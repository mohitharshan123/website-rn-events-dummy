# WebView Demo Page

A simple HTML page with buttons that send events to React Native WebView.

## Features

- Clean, modern UI with multiple interactive buttons
- Sends different types of events to React Native WebView
- Visual feedback when events are sent
- Responsive design that works on mobile devices

## Deployment to GitHub Pages

1. **Create a new repository on GitHub**
   - Go to GitHub.com and create a new repository
   - Name it something like `webview-demo` or `rn-webview-page`

2. **Upload files to your repository**
   - Upload the `index.html` file to your repository
   - Commit the changes

3. **Enable GitHub Pages**
   - Go to your repository Settings
   - Scroll down to "Pages" section
   - Under "Source", select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Click "Save"

4. **Access your deployed page**
   - Your page will be available at: `https://yourusername.github.io/repository-name/`
   - It may take a few minutes for the page to be live

## Using with React Native WebView

Once deployed, you can load this page in your React Native app using the `react-native-webview` package:

```javascript
import { WebView } from 'react-native-webview';

// In your component
<WebView
  source={{ uri: 'https://yourusername.github.io/repository-name/' }}
  onMessage={(event) => {
    const data = JSON.parse(event.nativeEvent.data);
    console.log('Received from WebView:', data);
    
    // Handle different event types
    switch (data.type) {
      case 'simple_event':
        console.log('Simple event:', data.message);
        break;
      case 'success':
        console.log('Success event:', data.message);
        break;
      case 'error':
        console.log('Error event:', data.message);
        break;
      case 'data_event':
        console.log('Data event:', data.payload);
        break;
      case 'page_ready':
        console.log('Page ready:', data.message);
        break;
    }
  }}
  javaScriptEnabled={true}
/>
```

## Event Types

The page sends these event types to React Native:

- `simple_event`: Basic event with a message
- `success`: Success event with message and timestamp
- `error`: Error event with message, code, and timestamp
- `data_event`: Complex event with user data payload
- `page_ready`: Sent automatically when the page loads

## Development

To test locally:
1. Open `index.html` in a web browser
2. Click the buttons to see the events in the browser console
3. The page will show error messages when not running in a WebView

## Customization

You can easily customize the page by:
- Modifying the button styles in the CSS
- Adding new buttons with different event types
- Changing the event data structure
- Adding more interactive elements 