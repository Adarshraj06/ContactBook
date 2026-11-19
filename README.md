# Contact Book App 📱

A simple Android Contact Book application built using **Kotlin, Jetpack Compose, Room Database, and Material 3**. The app allows users to save and view contacts locally on their device, with a maximum limit of three contacts.

## Features

- **Add Contacts:** Enter a contact's name and phone number.
- **Local Storage:** Save contacts using Room Database.
- **Contact Limit:** Allows a maximum of 3 contacts.
- **Input Validation:** Prevents saving contacts with empty fields.
- **Contact List:** Displays all saved contacts.
- **Automatic Updates:** The contact list updates when a new contact is saved.
- **Success and Error Messages:** Displays appropriate messages when adding contacts.

## Technologies Used

- **Kotlin** – Main programming language.
- **Jetpack Compose** – Declarative UI toolkit.
- **Material 3** – Modern Android UI components.
- **Room Database** – Local data persistence.
- **Kotlin Flow / StateFlow** – Reactive data handling.
- **ViewModel** – Manages UI-related data.
- **Coroutines** – Handles asynchronous database operations.
- **KSP** – Room database code generation.

## Application Architecture

The application follows the MVVM (Model-View-ViewModel) architecture.

```text
ContactBook
│
├── Contact.kt
│   └── Contact Entity
│
├── ContactDao.kt
│   └── Database Operations
│
├── ContactDatabase.kt
│   └── Room Database
│
├── ContactViewModel.kt
│   └── Business Logic
│
└── MainActivity.kt
    └── Jetpack Compose UI
```

*Note: The components are currently organized in MainActivity.kt in the provided implementation. They can be separated into individual files as the project grows.*

## How It Works

1. The user enters a name and phone number.
2. The user clicks the **Add Contact** button.
3. The ViewModel validates the input.
4. The application checks the number of existing contacts in Room Database.
5. If fewer than 3 contacts exist, the new contact is saved.
6. If 3 contacts already exist, insertion is blocked and a limit-reached message is displayed.
7. The saved contact list updates automatically using Kotlin Flow.

## Contact Limit Logic

The application uses the following condition:

```kotlin
if (dao.getContactCount() < 3) {
    dao.insertContact(contact)
} else {
    // Contact limit reached
}
```

The count check and insertion are performed inside a Room database transaction to maintain the three-contact limit safely.

## Database Structure

**Table Name:** `contacts`

| Column | Data Type | Description |
|---|---|---|
| id | Int | Auto-generated primary key |
| name | String | Contact name |
| phone | String | Contact phone number |

## Installation and Setup

1. Clone this repository:

   ```bash
   git clone https://github.com/YOUR-USERNAME/ContactBook.git
   ```

2. Open the project in Android Studio.

3. Allow Gradle to sync and download the required dependencies.

4. Run the application on an Android emulator or physical device.

## Assignment Details

- **Course:** Android App Deployment
- **Course Code:** CSE226
- **Academic Task:** Task 3
- **Topic:** Contact Book Application using Room Database
- **University:** Lovely Professional University

## Learning Outcomes

Through this project, I practised:

- Implementing Room Database using Entity, DAO, and Database components.
- Performing local CRUD-related database operations, particularly insertion and retrieval.
- Managing UI state using ViewModel and StateFlow.
- Using Kotlin Coroutines for asynchronous operations.
- Building responsive interfaces using Jetpack Compose and Material 3.
- Implementing database validation and transaction-based insertion limits.

---

**Developed as part of the Android App Deployment course.**
