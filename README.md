# BreezeDB


## Introduction

**BreezeDB** is a lightweight, fast, and flexible JSON-based database designed to handle multiple requests and threads simultaneously while consuming minimal RAM. Perfectly suited for small server environments, Electron.js applications, and projects where simplicity and efficiency are key. BreezeDB offers a straightforward API that requires no prior knowledge of SQL or complex database languages, making it accessible to developers of all skill levels.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
  - [Constructor](#constructor)
  - [Methods](#methods)
    - [insert](#insert)
    - [insertIfNotExist](#insertifnotexist)
    - [get](#get)
    - [getOne](#getone)
    - [update](#update)
    - [delete](#delete)
    - [count](#count)
    - [getRandom](#getrandom)
- [Dependencies](#dependencies)
- [License](#license)

## Features

- **Simple Setup**: No need to learn complex database languages. Start storing data immediately with a few lines of code.
- **Thread-Safe Operations**: Handles multiple threads and concurrent requests effortlessly, ensuring data integrity.
- **Dynamic Querying**: Break free from the limitations of traditional databases with our flexible and powerful query capabilities using callbacks. Tailor custom queries to your specific needs, without any limitations.
- **Low Resource Consumption**: Optimized for low-RAM environments, BreezeDB is perfect for small server configurations.
- **Scalable File Management**: Automatically manages large data sets by splitting them into multiple files to avoid performance degradation.
- **Minimal Dependencies**: Built with minimal dependencies, keeping your project lightweight and fast.

## Installation

You can install BreezeDB via npm:

```bash
npm install breezedb
```

## Usage
Here's a basic example demonstrating how to use BreezeDB:

```javascript
const BreezeDB = require('breezedb');

// Initialize the database
const db = new BreezeDB('path/to/database_folder', 'users_table');

// Insert data
db.insert({ id: 1, name: 'John Doe', age: 30 });

// Retrieve data
const users = db.get(user => user.age > 20);

// Update data
db.update(user => user.id === 1, (user) => ({ ...user, age: 31 }));

// Delete data
db.delete(user => user.id === 1);

// Count records
const count = db.count(user => user.age > 20);

// Get a random record
const randomUser = db.getRandom(user => user.age > 20, 1);
```

## API Reference

### Constructor

```javascript
new BreezeDB(dataBase, tableName, [filesSize])
```

- **dataBase**: `string` - The path to the database directory.
- **tableName**: `string` - The name of the table (subdirectory) within the database.
- **filesSize**:`number` (optional) - The maximum size (in bytes) for each file before a new file is created. Defaults to 3,000,000 bytes.

### Methods

#### insert

Inserts a single object or an array of objects into the database.

- **Parameters:**
  - **data:** `object` or `array` - The data to be inserted.
- **returns:** `boolean` Returns `true` if the data was inserted successfully, otherwise `false`.

- **Example:**
```javascript
// insert one element
db.insert({ id: 1, name: 'John Doe', age: 30 });
// insert many elements
data = [
  { id: 1, name: 'user name 1', age: 30 },
  { id: 2, name: 'user name 2', age: 25 },
  { id: 3, name: 'user name 3', age: 50 }
]
db.insert(data);
```











[![npm version](https://badge.fury.io/js/breezedb.svg)](https://badge.fury.io/js/breezedb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

