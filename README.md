# Flight Tracker App

An Android application that allows users to track real-time flight information using the Aviationstack API and stores the data locally with Room Database. It also keeps flight data updated in the background using WorkManager.

---

## Features

- Search flights by flight number using the Aviationstack API  
- Store flight details locally using Room Database  
- Automatically update flight logs using background jobs  
- Parse JSON responses with GSON  
- Built using MVVM architecture with Retrofit and Room

---

## Local Database (Room)

- The app uses Room to persist flight data locally.
- A `FlightLog` entity defines the schema for the `flightlog` table.
- `AppDatabase` is a singleton class providing access to the DAO (`FlightLogDao`).

---

## Inserting and Retrieving Data

- The `FlightLogDao` interface includes methods for:
  - Inserting new flight records  
  - Fetching analytics like average flight duration
- All database operations are handled asynchronously using Kotlin coroutines for a responsive UI.

---

## Background Sync with WorkManager

- WorkManager ensures the app stays updated even when not in use.
- `FlightWorker` is a `CoroutineWorker` that:
  - Fetches updated flight data from the API
  - Updates local records in the database

---

## API Integration with Retrofit

- `RetrofitClient` sets the base URL for the Aviationstack API.
- GSON is used for seamless conversion of JSON to Kotlin objects.
- The `AviationApi` interface contains the GET endpoint for retrieving flight information based on flight number and API key.

---

## JSON Response Parsing

- API responses are parsed into data classes like `FlightResponse` using GSON.
- These models mirror the API's JSON structure and are used across the app to manage and display flight data.

---
