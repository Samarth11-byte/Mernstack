# MERN CRUD Item Manager

A small CRUD application based on the form and table in the supplied sketch. It lets you create, read, update and delete items with a name and price.

## Tech stack

- **MongoDB** — stores the items
- **Express.js + Node.js** — provides the REST API
- **React** — renders the form and table
- **Vite** — runs/builds the React frontend

## Requirements

- Node.js 18 or later and npm
- MongoDB Community Server running locally, or a MongoDB Atlas connection string

## Run locally

1. Extract the ZIP and open a terminal in the `mern-crud-items` folder.
2. Install all dependencies from the project root:

   ```bash
   npm install
   ```

3. Create `server/.env` by copying `server/.env.example`. The default URI works when MongoDB is running on your own computer:

   ```env
   PORT=5000
   MONGODB_URI=mongodb://127.0.0.1:27017/mern_crud_items
   ```

   For MongoDB Atlas, replace `MONGODB_URI` with your Atlas connection string.

4. Start both the Express API and React development server:

   ```bash
   npm run dev
   ```

5. Open **http://localhost:5173** in your browser.

The first start inserts sample records `Book — 250` and `Pen — 25` if the database is empty. Existing database records are not overwritten. To prevent sample seeding, set `SEED_SAMPLE_DATA=false` in `server/.env`.

## REST API

Base URL (through the Vite proxy during development): `/api/items`

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `GET` | `/api/items` | Get all items |
| `POST` | `/api/items` | Add an item |
| `PUT` | `/api/items/:id` | Update an item by MongoDB ID |
| `DELETE` | `/api/items/:id` | Delete an item by MongoDB ID |
| `GET` | `/api/health` | Check whether the API is running |

Example JSON body for POST and PUT:

```json
{
  "name": "Notebook",
  "price": 80
}
```

## CRUD flow

1. **Create:** enter a name and price, then click **Add item**.
2. **Read:** saved items load into the table from `GET /api/items`.
3. **Update:** click **Edit**, change the form values, and click **Save changes**. Use **Cancel** to leave edit mode.
4. **Delete:** click **Delete** and confirm the prompt.

## Project structure

```text
mern-crud-items/
├── client/
│   ├── src/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── styles.css
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
├── server/
│   ├── src/
│   │   ├── models/Item.js
│   │   ├── routes/itemRoutes.js
│   │   └── index.js
│   ├── .env.example
│   └── package.json
├── .gitignore
├── package.json
└── README.md
```
