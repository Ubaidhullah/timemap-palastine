<h1 align="center">
  Palestine Timemap v0
</h1>

<p align="center">
  <strong>The Palestine Timemap is a tool for exploration, monitoring, and classification of incidents in time and space, focusing on the ongoing conflict and its devastating impacts since October 2023.<br>See a <a href="https://blmprotests.forensic-architecture.org">live instance here</a>.</strong><br>
</p>

![](docs/example-timemap.png)

[![Build status](https://travis-ci.com/forensic-architecture/timemap.svg?branch=develop)](https://travis-ci.com/forensic-architecture/timemap)

## Overview

The Palestine Timemap is a standalone frontend application that allows you to explore and monitor events in time and space. It uses OpenStreetMap satellite imagery as a backdrop by default, but can also be configured to use [mapbox](https://www.mapbox.com/). It utilizes Leaflet and d3 to visually map information.

The recommended way to run a backend for the Palestine Timemap is using [datasheet-server](https://github.com/forensic-architecture/datasheet-server). This allows you to work with a spreadsheet or Google Sheet as a dynamic database for the timemap.

The Palestine Timemap has the following high-level features:

- Visualize incidents of particular events on a map.
- Visualize and filter these incidents over time, on an adjustable timeline that allows zooming in and out.
- Visualize types of incidents by tag and by category, which can be displayed using different styles.

A fully-functioning live version can be found as a result of the Forensic Architecture investigation of the [Battle of Ilovaisk](https://ilovaisk.forensic-architecture.org).

## Project Overview

The timemap provides a detailed chronological account of incidents, categorized by events, regions, and affected communities. It seeks to offer a comprehensive and accessible resource for understanding the scale and nature of the conflict, the human rights violations, and the humanitarian crisis resulting from the ongoing violence.

## Features

- **Interactive Map**: Explore events geographically to see where incidents have occurred.
- **Timeline**: View the sequence of events over time to understand the progression of the conflict.
- **Categories**: Filter events by different categories such as civilian casualties, infrastructure damage, and humanitarian responses.
- **Narratives**: Read detailed narratives that provide context and personal stories behind the events.

## Purpose

This timemap is created to raise awareness, provide reliable information, and support efforts towards justice and peace. By documenting the atrocities and their impacts, we hope to contribute to a more informed public discourse and advocate for the protection of human rights.

## How to Use

Navigate through the map to explore specific incidents, use the timeline to see how events have unfolded, and dive into the narratives for in-depth stories.

## Get up and running

The easiest way to get up and running with the Palestine Timemap and datasheet-server is to [follow the in-depth tutorial here](https://forensic-architecture.org/investigation/timemap-for-cartographic-platforms).

We recommend using **Node v16.x.x** for its current compatibility. The timemap may not work with other versions of Node.

### Quickstart

1. Pull this repository.

```shell
git clone https://github.com/forensic-architecture/timemap
```

2. Install dependencies via npm.

```shell
npm install
```

3. Copy the example config

```shell
cp example.config.js config.js
```

4. Run the development server, which will be available at http://localhost:8080.

```shell
CONFIG=config.js npm run dev
```

To run with a file that is not 'config.js' in the root directory, set the `CONFIG` environment variable:

```
CONFIG="myotherconfig.js" npm run dev
```

At this stage, you'll probably only see a basic map with several error modals. In order for TimeMap to be able to display interesting information, you'll have to make sure to have the capacity to serve data, as well as adjusting some configuration parameters. 


#### Running without datasheet-server

Technically, timemap is backend agnostic, but it requires a series of endpoints to provide data for it to visualize. The data is expected in JSON format. Some data elements are required and their format has some required fields. Other additional endpoints are optional, and if enabled, they simply add features to your taste.

The combination of all these data types is called the `domain` of the application in the context of TimeMap.

#### Running tests

We are currently using [Jest](https://jestjs.io/) for front-end and component testing. These tests can be found inside `src/test`. The test suite can be invoked through `CONFIG="my-optional-config.js" npm run test`.

We also include an [Ava](https://github.com/avajs/ava) test suite for smoke testing the Node server process responsible for instantiating the app. This test suite can be invoked using `CONFIG="my-optional-config.js" npm run test:ava`
