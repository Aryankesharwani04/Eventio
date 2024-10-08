# Eventio

Eventio is a web application for booking events, movies, and shows. This document explains the high-level and low-level design, along with functional and non-functional requirements, user stories, and system design patterns used in Eventio.

## High-Level Design

1. **Class for Eventio**:
   - Manages overall system functionality.
   
2. **Class for Event**:
   - Represents individual events, shows, or movies.
   
3. **Class for Attendee**:
   - Represents users attending events.
   
4. **Class for Ticket**:
   - Manages ticket booking and allocation for events.

## Low-Level Design

### 1. **Eventio Class**
   - **Attributes**:
     - `events`: List of all events.
   - **Methods**:
     - `add_event(Event)`: Adds a new event.
     - `remove_event(EventID)`: Removes an event by its ID.
     - `get_all_events()`: Returns a list of all events.
     - `get_event_by_id(EventID)`: Returns a specific event by its ID.
     - `get_attendees_for_event(EventID)`: Returns all attendees for a specific event.
     - `get_tickets_for_event(EventID)`: Returns all tickets for a specific event.
   
### 2. **Event Class**
   - **Attributes**:
     - `name`: Name of the event.
     - `date`: Date of the event.
     - `attendees`: List of attendees.
     - `tickets`: List of tickets associated with the event.
   - **Methods**:
     - None explicitly mentioned but should manage attendee and ticket association.

### 3. **Attendee Class**
   - **Attributes**:
     - `name`: Name of the attendee.
     - `email`: Email of the attendee.
     - `ticket`: The ticket associated with the attendee.
   
### 4. **Ticket Class**
   - **Attributes**:
     - Ticket-related properties (seat number, price, etc.).

## Functional Requirements

- **User Management**: Register, login, and logout.
- **Event Search**: Search for shows by movie name, theater, or event.
- **Location Integration**: Show events based on the user’s location.
- **Booking**: Book tickets for shows or events.

## Non-Functional Requirements

- **Scalability**: System should handle a high volume of users and bookings.
- **Performance**: Real-time event search and booking should be fast and reliable.
- **Security**: Secure user authentication and data protection.

## User Stories for Eventio

### As a User:
- I want to **register** so that I can create an account.
- I want to **login** to access my account.
- I want to **search for shows** by movie name or theater.
- I want to **book a ticket** for a show.
- I want to **see event details** before booking.
- I want to **cancel my booking** if needed.

### As an Admin:
- I want to **add events** to the platform.
- I want to **remove events** when they are no longer available.
- I want to **see all attendees** for an event.
- I want to **manage tickets** for events.

## Identifying Entities

### 1. **User**
   - Attributes: `name`, `email`, `password`
   - Operations: Register, login, logout

### 2. **Movie**
   - Attributes: `title`, `genre`, `director`, `release_date`
   - Operations: Search, book
   
### 3. **Theater**
   - Attributes: `name`, `location`, `capacity`
   - Operations: Show available movies, book tickets
   
### 4. **Show**
   - Attributes: `showtime`, `theater`, `movie`
   - Operations: Book tickets, cancel booking
   
### 5. **Booking**
   - Attributes: `user`, `show`, `status`
   - Operations: Confirm booking, cancel booking

## Relationships

- **User** can book a **Show**.
- **Show** belongs to a **Movie** and happens in a **Theater**.
- **User** can book multiple **Tickets** for different **Shows**.

## Operations

- **User**: Register, login, logout.
- **Movie**: Search, list showtimes, display details.
- **Theater**: Show available shows, allow ticket booking.
- **Show**: Book or cancel tickets.

## Constraints

- **User**: Can book only available shows.
- **Show**: Limited seating capacity for booking.
- **Theater**: Capacity constraints for booking multiple shows.

---

### Classes in the Application

1. **Person (Class)**
   - **Attributes**: `name`, `age`, `gender`, `occupation`
   - **Methods**: `login()`, `logout()`, `register()`
   
2. **Movie (Class)**
   - **Attributes**: `title`, `genre`, `director`, `release_date`
   - **Methods**: `search()`, `book()`
   
3. **Show (Class)**
   - **Attributes**: `showtime`, `theater`, `movie`
   - **Methods**: `book()`, `cancel()`
   
4. **Theater (Class)**
   - **Attributes**: `name`, `location`, `capacity`
   - **Methods**: `book()`, `cancel()`

5. **ShowTime (Independent Object)**
   - **Attributes**: `time`, `date`

6. **Booking (Class)**
   - **Attributes**: `user`, `show`, `status`
   - **Methods**: `confirm()`, `cancel()`

---