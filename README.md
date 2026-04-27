# FREENOW Driver Activity & Performance Analysis

## What this project is about

This project focuses on cleaning the raw data and building a dataset to analyze driver behavior, operations performance, and trip outcomes.

---

## Data cleaning

The origianl tables provided are:

* `freenow_drivers`
* `freenow_bookings`
* `freenow_offers`

### What was cleaned:

**Drivers**

* Standardized country names
* Converted ratings and counts to numeric
* Fixed date formats
* Cleaned boolean fields (receive_marketing)

**Bookings**

* Converted fare to numeric (`estimated_fare_eur`)
* Removed invalid or extreme values "for example some cells havd enormous fare values"
* Standardized datetime
* Kept all booking statuses

**Offers**

* Removed duplicate rows
* Filtered invalid route distances (for example negative values)
* Standardized states (ACCEPTED, CANCELLED)
* Cleaned `driver_read` (0/1)

### Clean new tables:

* `drivers_final`
* `bookings_final`
* `offers_final`

---

## Main table

The final table **`driver_daily_activity`** was created from the 3 cleaned tables.

### Main Table key idea:

* One row per **driver per day**
* Covers **01.06.2021 → 14.06.2021**
* Includes drivers even with **no activity**

### What it contains:

* Driver info (driver_id, country, date)
* Offer data (offers, accepted, read, ignored)
* Booking data (bookings, success, aborts)
* Revenue

---

## Metrics

From this table, the following calculations were made:

### Driver engagement

* Offer read rate
* Acceptance rate
* Ignored rate

### Operations efficiency

* Offer → booking conversion
* Acceptance → booking conversion

### Trip outcomes

* Completion rate
* Abort rates (driver, passenger, system, no driver)
* Failure rate

### Revenue

* Revenue per booking
* Revenue per driver per day

---

## What this enables

* Funnel analysis (offers → bookings → completed trips)
* Driver performance analysis
* Country-level comparisons
* Identifying inefficiencies in the marketplace

---
