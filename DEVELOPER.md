# A Real-time Geo-social Media Database for Large-scale Coronavirus Disease 2019 (COVID-19) Research

Richard Wen rwen@ryerson.ca  
  
Developer notes for presentation slides.

## Install

1. Install [Node.js](https://nodejs.org/en/)
2. Install [git](https://git-scm.com/)
3. Change directory `cd` into project folder
4. Install required packages with `npm`

```
git clone https://github.com/rrwen/slides-covid19-geosocial-db
cd slides-covid19-geosocial-db
npm install
```

## Usage

### Serving Slides

Build slides into [docs/](docs/) folder:

```
npm run build
```

Then, serve them with `https-server`:

```
npm run server
```

### Reveal.js Plugins

Install or remove a `bower` plugin into [docs/plugin](docs/plugin/) folder:

```
npm run install-plugin <plugin-name>
npm run remove-plugin <plugin-name>
```

Then edit [template.html](template/template.html) accordingly.
