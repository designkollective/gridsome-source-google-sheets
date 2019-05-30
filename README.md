# Gridsome Source for Google Sheets

Source plugin for fetching data from Google Sheets. 

## Install 

```js
yarn add gridsome-source-google-sheets
```
npm
```js
npm install gridsome-source-google-sheets
```

## How to use

You will need to generate a google api key [here](https://console.developers.google.com/apis/credentials). The sheetId can be found on the sheets url. You will also need to make your spreadsheet viewable to the public to use the api credentials.
```js
module.exports = {
  siteName: 'Gridsome',
  plugins: [
    {
      use: 'gridsome-source-google-sheets',
      options: {
        sheetId: 'GOOGLE_SHEET_ID', 
        apiKey: 'GOOGLE_API_KEY',
        route: 'OPTIONAL_ROUTE', //Omit if not using routes
      }
    }
  ]
}
```

## Example query on pages

```js
<page-query>
  query MyData {
    allGoogleSheets {
      edges {
        node {
          Col1
          Col2
        }
      }
    }
  }
</page-query>
```

## Example query in GoogleSheet template

```js
<page-query>
query Post ($path: String!) {
  googleSheet (path: $path) {
    col1
    col2
  }
}
</page-query>
```