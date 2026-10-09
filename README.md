# StockLite - Warehouse Inventory System

StockLite is a small warehouse inventory app that tracks products across two warehouses, lets staff record stock movements, and keeps a history of every transaction. This starter project provides the UI, seed data, and basic app structure. Your job is to make it actually work.

## Overview

StockLite is a starter project for a warehouse inventory system. It is designed to help staff:

- View products and their stock levels across two warehouses
- Record stock coming in and going out
- Transfer stock between warehouses
- Review a history of every transaction

The UI, seed data, and app structure are already in place, but none of the actual inventory logic is implemented. Participants are expected to build the logic that makes the application work.

## What Has Already Been Built

The starter project already includes the following functionality. Participants should build the remaining functionality described in the tasks below.

- **Inventory grid UI** (`/`): a styled inventory grid
- **Stock In / Stock Out form UI** (`/stock`)
- **Warehouse Transfer form UI** (`/transfer`)
- **Transaction History page UI** (`/history`)
- **Seed data** (`lib/seed-data.ts`): a seeded in-memory store with ~20 products across 2 warehouses, including products above, near, and at their reorder threshold
- **Auth skeleton** (`/login`, `lib/auth.ts`): not real authentication, just the expected shape
- **Stubbed API routes**: `GET /api/items` and `GET /api/transactions`, which return the seeded data as-is
- **UI components** (`components/`): table, forms, status badge, and navigation
- **Shared types** (`lib/types.ts`)

## Features

### Existing Features

- Inventory, Stock In / Stock Out, Warehouse Transfer, and Transaction History pages with styled UI
- Seeded products, warehouses, and transactions in an in-memory store
- Staff login skeleton
- Stubbed read-only API routes for items and transactions

### Features to Be Implemented

- Inventory view with category and low stock filtering
- Stock In and Stock Out with validation and transaction logging
- Warehouse transfers between the two warehouses
- Transaction history with filtering and sorting
- Bug fixes for stock totals, negative inventory, transfers, and low stock status
- _(Stretch)_ Low stock summary panel per warehouse

None of the inventory logic (filtering, validation, stock mutation, transfers, or transaction recording) is implemented yet.

## Tech Stack

- **Language:** TypeScript
- **Framework:** Next.js (App Router)
- **UI:** React components
- **Data storage:** Seeded in-memory store (`lib/seed-data.ts`)
- **Package manager:** npm

## Getting Started

### 1. Fork the Repository

Fork this repository to your own GitHub account using the **Fork** button at the top of the repository page.

### 2. Clone the Repository

Clone your fork to your local machine:

```bash
git clone <your-forked-repository-url>
```

### 3. Install Dependencies

```bash
npm install
```

### 4. Run the Application

```bash
npm run dev
```

Then open [http://localhost:3000](http://localhost:3000).

## Project Structure

```text
app/
├── page.tsx                    # Inventory View
├── stock/page.tsx              # Stock In / Stock Out
├── transfer/page.tsx           # Warehouse Transfer
├── history/page.tsx            # Transaction History
├── login/page.tsx              # Auth skeleton
└── api/
    ├── items/route.ts          # Stubbed items API
    └── transactions/route.ts   # Stubbed transactions API
components/                     # UI components (table, forms, status badge, nav)
lib/
├── seed-data.ts                # Seeded products, warehouses, transactions
├── types.ts                    # Shared types
└── auth.ts                     # Stubbed staff user
```
### Task 1 — Inventory View

- Display name, category, warehouse, current stock, and reorder threshold
- Filter by category
- Filter by low stock only
- Apply the correct low stock rule: current stock ≤ threshold
- Ensure the category and low stock filters combine correctly
- Handle the empty state gracefully

### Task 2 — Stock In and Stock Out

- Make the stock in form and API increment the correct warehouse
- Make the stock out form and API decrement the correct warehouse
- Block a stock out that would exceed current stock
- Reject invalid quantities (zero, negative, non-numeric)
- Ensure the UI reflects the new stock level immediately
- Log the operation for transaction history

### Task 3 — Warehouse Transfer

- Provide a transfer form with product, source warehouse, destination warehouse, and quantity
- Deduct the quantity from the source warehouse
- Add the quantity to the destination warehouse
- Reject a transfer if the source has insufficient stock
- Validate both warehouses before writing, so no partial transfer applies on failure
- Record the transfer as a linked pair in the transaction history

### Task 4 — Transaction History

- List transactions with product, warehouse, type, quantity, and timestamp
- Filter by transaction type
- Filter by warehouse
- Sort by most recent timestamp
- Ensure the filters combine correctly

## Debugging Tasks

### Task 5 — Debugging

Fix the following issues:

- Incorrect stock totals after operations
- Negative inventory being allowed
- A transfer that only updates one warehouse
- Incorrect low stock status logic

This is the task that was asked us to modify.
