# wandejaunt-org-chart

## Project Description

Retrieve a list of Employees from the /employee endpoint and display them as a nested list.
*Your submission should render in the browser (A single index.html file with all your code is fine, as is a Django view, or anything else).*

<ol>
  <li> Employees are displayed with full name and title. </li>
  <li> Employees are nested underneath the manager they report to. </li>
  <li> When a manager has more than one report, sort reports alphabetically by last name </li>
</ol>

### Example endpoint response

```javascript
[
  { "name": "Barrett Glasauer", "id": 1, "title": "CTO", "manager_id": 2 },
  { "name": "Michael Chen", "id": 2, "title": "CEO", "manager_id": null },
  { "name": "Julian Early", "id": 3, "title": "Engineer", "manager_id": 8 },
  { "name": "Andres Green", "id": 4, "title": "COO", "manager_id": 2 }, 
  { "name": "Emily Pun", "id": 5, "title": "Designer", "manager_id": 32 },
  { "name": "Michael Lorton", "id": 6, "title": "Engineer", "manager_id": 8 },
  { "name": "Chris Hancock", "id": 8, "title": "Engineering Manager", "manager_id": 1 },
  { "name": "Shrutika Dasgupta", "id": 22, "title": "Engineer", "manager_id": 8 },
  { "name": "Ryan Miller", "id": 30, "title": "Head of Operations", "manager_id": 4 },
  { "name": "Natasha Prats", "id": 32, "title": "Head of Product", "manager_id": 2 },
  { "name": "Mauricio Aizaga", "id": 33, "title": "Engineer", "manager_id": 8 }
]
```

### Example expected output

<ul>
    <li> CEO: Michael Chen
        <ul>
            <li>CTO: Barrett Glasauer
                <ul>
                    <li> Engineering Lead: Chris Hancock
                        <ul>
                            <li> Engineer: Shrutika Dasgupta</li>
                            <li> Engineer: Shrutika Dasgupta</li>
                        </ul>
                    </li>
                </ul>
            </li>
            <li>COO: Andres Green
                <ul>
                    <li>Operations Lead: Ryan Miller</li>
                </ul>
            </li>
        </ul>
    </li>
</ul>

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
