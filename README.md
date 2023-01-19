# Search Countries

Build a countries search page

## Live Example

See [demo app](https://incandescent-faloodeh-ac6db8.netlify.app/)

## Getting Started

Use [this repository](https://github.com/alchemycodelab/half-baked-web-01-countries-search) as a template for this deliverable.


### Supabase

#### `<script>`

Add in the following `<script>` tag to `index.html` for supabase functionality:

```html
<!-- js -->
<script
    defer
    src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@1.35.7/dist/umd/supabase.min.js"
></script>
<!-- goes before this one: -->
<script type="module" src="app.js"></script>
```

#### `fetch-utils.js`

Create a `fetch-utils.js` file at the root of your project. Use the following setup for
creating a supabase client to the Beanie Babies project:

```js
const SUPABASE_URL = "https://gxwgjhfyrlwiqakdeamc.supabase.co";
const SUPABASE_KEY =
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiYW5vbiIsImlhdCI6MTYzNjQxMTMxMiwiZXhwIjoxOTUxOTg3MzEyfQ.PHekiwfLxT73qQsLklp0QFEfNx9NlmkssJFDnlvNIcA";

const client = supabase.createClient(SUPABASE_URL, SUPABASE_KEY);

// export async functions that fetch data
```


Here's how we fetch all beanie babie from the beanie_babies table, assuming you've copied the above code correctly:
```js
let { data, error } = await client
    .from('beanie_babies')
    .select('*');
```

Here's a special this-project-only way of get a list of astrological signs:
```js
    let { data, error } = await client
        .from('beanie_baby_astro_signs')
        .select('*');
```

## Learning Objectives

-   On load, use fetch and async/await to hit a GET endpoint, get all items, and set state and update the view using the response
-   Write a supabase query table to return specified information
-   Use a form to capture the user input; use FormData in queries

## Description of functionality

-   Load and display basic country data:

    -   `getCountries` fetch call in `fetch-utils.js`
    -   Import, load event, findCountries, displayCountries in `app.js`

-   Populate continents dropdown:

    -   `getContinents` service call in `fetch-utils.js`
    -   Import, load event, displayContinentOptions in `app.js`

-   Search Countries:
    -   Add query logic in `getCountries` in `fetch-utils.js`
    -   Form event, findCountries in `app.js`

## App Requirements

Present a search form to the user and shows a list of up to the first 100 countries that match the search.

Search on:

| Attribute | Search                        |
| --------- | ----------------------------- |
| continent | `.eq('continent', continent)` |

## Rubric

The following is required for your assignment to be graded:

-   PR open from `dev` to `main`
-   PR Passes CI (lint + tests)
-   PR preview on netlify
-   At least 3 commits (for the individual working features)

| Events...                                                       | **10** |
| --------------------------------------------------------------- | ------ |
| All countries display on page load                              | 3      |
| Populate continent dropdown from supabase fetch (not hardcoded) | 4      |
| Search based on Continent dropdown                              | 3      |

## Data Model

Here is the model for the `countries` table:

![data model](./data-model.png)

In addition to the table, there is a view you can use to get attributes for dropdown lists:

| Attribute | View name            | Object structure            |
| --------- | -------------------- | --------------------------- |
| continent | `country_continents` | `{ name: 'North America' }` |
