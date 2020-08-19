# Parse Google Docs JSON

This **Node.js** module authenticates with **Google API** and parse **Google Docs** to human-readable **JSON** or **Markdown** without the need to use cumbersome methods like exporting it in HTML via **Google Drive API** and then parse it back to other formats.

# Why

When you use **Google Docs API V1**, the [body](https://developers.google.com/docs/api/reference/rest/v1/documents#Body) that comes with the `documents.get` method is completely fragmented. It's a JSON that you need to recursively parse to get the document into human-readable format. For my luck, there's a Gatsby plugin that internally has this implementation already: [gatsby-source-google-docs](https://github.com/cedricdelpoux/gatsby-source-google-docs). So I've extracted this implementation into this module and exposed it with a **Service Authentication**. For more information about this type of authentication, follow this tutorial: [How to authenticate to any Google API](https://flaviocopes.com/google-api-authentication)

# Warning

This module works like a charm, but it's for personal use, primarily. It will follow semantic version best practices, but will not have any automated tests in the short term.

# How to use

```js
const parseGoogleDocsJson = require("parse-google-docs-json");

async function start() {
  const parsed = await parseGoogleDocsJson({
    documentId: "1ymKw2OGcMfc02XdEEWdy22a_zUAlCxyN3P5Ab4c",
    clientEmail: "service@iam.gserviceaccount.com",
    privateKey: "-----BEGIN PRIVATE KEY...",
  });

  console.log(parsed.toJson());
  console.log(parsed.toMarkdown());
}

start();
```

# Environment variables

```
clientEmail = process.env.PARSE_GOOGLE_DOCS_CLIENT_EMAIL
privateKey = process.env.PARSE_GOOGLE_DOCS_PRIVATE_KEY
```
