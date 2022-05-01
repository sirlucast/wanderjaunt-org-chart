# wandejaunt-org-chart

## Project Description

Retrieve a list of Employees from the /employee endpoint and display them as a nested list.
*Your submission should render in the browser (A single index.html file with all your code is fine, as is a Django view, or anything else).*

<ol>
  <li> Employees are displayed with full name and title. </li>
  <li> Employees are nested underneath the manager they report to. </li>
  <li> When a manager has more than one report, sort reports alphabetically by last name </li>
</ol>

employee list API [here](https://gist.githubusercontent.com/chancock09/6d2a5a4436dcd488b8287f3e3e4fc73d/raw/fa47d64c6d5fc860fabd3033a1a4e3c59336324e/employees.json).


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
