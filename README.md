# Local Event Finder

## **Table of Contents**
1. Overview
2. Product Spec
3. Wireframes
4. Schema


---

## **Overview**

### **Description**  
Local Event Finder is a mobile application that allows users to discover and explore events happening around their location. Users can log in, view event details, and personalize their experience with optional features like saving events, searching by filters, and receiving notifications for saved events.

### **App Evaluation**
- **Category**: Entertainment / Social
- **Mobile**: The app is designed exclusively for mobile devices to ensure on-the-go access to event details.
- **Story**: Helps users discover local events and plan their activities with ease.
- **Market**: Targeted at anyone looking for local events, including young adults, families, and travelers.
- **Habit**: Likely used occasionally, based on when users need event recommendations.
- **Scope**: Focused on event discovery and details with potential to expand into event management features.

---

## **Product Spec**

### **1. User Stories**

#### **Required Must-have Stories**  
1. **User can register for an account.**
2. **User can log in to their account.**
3. **User can view a list of events based on their location.**
4. **User can view detailed information about an event.**

#### **Optional Nice-to-have Stories**  
1. **User can save an event to their favorites.**
2. **User can search for events using filters (e.g., date, category).**
3. **User can receive notifications about saved events or updates.**

---

### **2. Screen Archetypes**

1. **Registration Screen**  
   - User can create a new account by providing their email, password, and additional details if required.

2. **Login Screen**  
   - User can log in to their account with email and password.

3. **Event List Screen**  
   - Displays a list of events based on the user’s location.

4. **Event Detail Screen**  
   - Provides detailed information about a selected event.

5. **Favorites Screen (Optional)**  
   - Shows a list of saved events.

6. **Search/Filter Screen (Optional)**  
   - Allows users to search for events by filters such as date or category.

---

### **3. Navigation**

#### **Tab Navigation (Tab to Screen)**
- **Home**: Displays the list of events.
- **Favorites**: (Optional) Shows saved events.
- **Search**: (Optional) Access filters and search functionality.

#### **Flow Navigation (Screen to Screen)**
- **Registration Screen** → Leads to **Home** (Event List) after successful account creation.
- **Login Screen** → Leads to **Home** (Event List) after successful login.
- **Home (Event List)** → Leads to **Event Detail Screen** when an event is selected.
- **Event Detail Screen** → Optionally leads to **Save Event** or returns to **Home**.
- **Favorites Screen** → Leads to **Event Detail Screen** for a saved event.
- **Search/Filter Screen** → Displays **Filtered Event List** → Leads to **Event Detail Screen**.

---

### **Wireframes**

- **Registration Screen**
  - Fields for username, email, and password.
  - "Sign Up" button.

- **Login Screen**
  - Email and password fields.
  - "Login" and "Forgot Password?" links.

- **Event List Screen**
  - A list view of events with event titles, dates, and short descriptions.
  - Navigation tabs (e.g., Home, Favorites, Search).

- **Event Detail Screen**
  - Event title, date, time, location, and description.
  - Buttons for "Save Event" and "Share".

- **Favorites Screen (Optional)**
  - A list of saved events.

- **Search/Filter Screen (Optional)**
  - Filters for location, date, category, etc.

---

#### **[BONUS] Digital Wireframes & Mockups**

#### **[BONUS] Interactive Prototype**

---

## **Schema**

### **Model: User**

| Property    | Type   | Description                                    |
|-------------|--------|------------------------------------------------|
| userId      | String | Unique identifier for the user.                |
| username    | String | User's display name.                           |
| email       | String | User's email address.                          |
| password    | String | Hashed password for authentication.           |

### **Model: Event**

| Property    | Type   | Description                                    |
|-------------|--------|------------------------------------------------|
| eventId     | String | Unique identifier for the event.               |
| title       | String | Title of the event.                            |
| date        | Date   | Date and time of the event.                    |
| location    | String | Address or venue of the event.                 |
| description | String | Detailed description of the event.             |
| isFavorite  | Boolean| Indicates if the event is saved by the user.   |

---

## **Networking**

### **List of Network Requests by Screen**

#### **Registration Screen**  
- **[POST] /register** – Register a new user.  

#### **Login Screen**  
- **[POST] /login** – Authenticate user and retrieve a session token.

#### **Event List Screen**  
- **[GET] /events** – Fetch a list of events near the user's location.

#### **Event Detail Screen**  
- **[GET] /events/:id** – Retrieve detailed information for a specific event.  
- **[POST] /favorites** – Save an event to the user's favorites.

#### **Favorites Screen**  
- **[GET] /favorites** – Retrieve the list of saved events.

#### **Search/Filter Screen**  
- **[GET] /events?filters** – Fetch events based on search filters.

---

### **Basic Network Snippets**

#### **Register User**

```swift
let parameters = ["email": email, "password": password]
AF.request("https://api.localfinder.com/register", method: .post, parameters: parameters, encoding: JSONEncoding.default).responseJSON { response in
    print(response)
}
