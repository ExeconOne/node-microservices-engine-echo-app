# @archimedes/httpecho

## Description
`@archimedes/httpecho` is a simple echo service that listens for HTTP requests and responds with specific headers that match a given condition.

## Installation
To install the module, run:
```bash
npm install @archimedes/httpecho
```

## Usage
To use the module, import it and initialize it with your application, base path, database, and logger.

```javascript
import httpecho from '@archimedes/httpecho';
import express from 'express';
import sqlite3 from 'sqlite3';
import { open } from 'sqlite';

const app = express();
const basePath = '/echo';
const logger = console;

(async () => {
    const appDb = await open({
        filename: '/path/to/database.db',
        driver: sqlite3.Database
    });

    httpecho(app, basePath, appDb, logger);

    app.listen(3000, () => {
        logger.log('Server is running on port 3000');
    });
})();
```

## Functionality
The service initializes a database table if it does not exist and sets up an endpoint that listens for HTTP requests. It filters the headers that start with `x-adi` and responds with those headers.

## Scripts
- `publish-patch`: Bumps the patch version, pushes the changes to the origin, and tags the commit.

## License
This project is licensed under the ISC License.