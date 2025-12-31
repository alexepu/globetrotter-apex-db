# globetrotter-apex-db

# Database Project Description: City Break Planner

## Overview

The chosen theme for this database project is a **City Break Management System**, built using Oracle APEX. It is designed to manage urban destinations, tourist attractions, travelers, and their visits. The database stores detailed information about cities, specific landmarks or activities, tourists, and the status of their trips (planned or completed), enabling efficient data organization and analysis of travel preferences and ratings.
![schema_apex](https://github.com/user-attachments/assets/d86b62bc-b85c-4fae-9b08-d12913d7ba44)

## Tables and Their Roles

### 1. TRAVEL_CITIES
This table represents the core destinations available in the system. It acts as the "Master" table for geographic locations, storing the city name, the country it belongs to, and the specific region (e.g., Western Europe, Asia). This structure allows for grouping destinations based on their location.
* **Example:** *Paris* is a city in *France*, located in the *Western Europe* region.

### 2. TRAVEL_ATTRACTIONS
This table contains specific tourist objectives linked to a particular city through `city_id`. It includes details such as the attraction name, its type (e.g., Museum, Landmark, Park), and the ticket price. This table serves as the "Product" or "Service" inventory of the application.
* **Example:** *The Eiffel Tower* is a Landmark located in *Paris*, with a specific ticket price.

### 3. TRAVEL_TOURISTS
This table stores personal information about the travelers using the system. It includes essential data such as first name, last name, email address, and their country of origin. This table acts as the central repository for customer data.

### 4. TRAVEL_VISITS
This is the central transaction table that records the interaction between tourists and attractions. It functions as a junction table to resolve the Many-to-Many relationship between Tourists and Attractions. It stores the date of the visit, the current status (e.g., 'Planned', 'Completed'), and a satisfaction rating (1-5).
* **Role:** It acts simultaneously as a **Booking** system (via the `status` and `visit_date` columns) and a **Review** system (via the `rating` column).

## Relationships Between Tables

* **TRAVEL_CITIES → TRAVEL_ATTRACTIONS:** One city can host multiple tourist attractions (1:M).
* **TRAVEL_ATTRACTIONS → TRAVEL_VISITS:** One attraction can receive multiple visits from different tourists (1:M).
* **TRAVEL_TOURISTS → TRAVEL_VISITS:** One tourist can make multiple visits to different attractions (1:M).
* **TRAVEL_TOURISTS ↔ TRAVEL_ATTRACTIONS:** A Many-to-Many (M:M) relationship exists between tourists and attractions, facilitated through the `TRAVEL_VISITS` table.

## APEX Application Features
The database supports an Oracle APEX application including:
* **Interactive Reports & Forms:** For managing cities, tourists, and visits.
* **Dashboard:** Visualizing data via Bar Charts (Attractions per City) and Pie Charts (Visit Status).
* **Calendar:** A visual representation of scheduled visits.
* **Validations & Computations:** Business logic to ensure data integrity (e.g., date validation) and automatic price calculations.
