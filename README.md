# Library Management System

A console-based Java application for managing a personal book collection. Supports data loading, persistence, multiple sorting algorithms, keyword search, and detailed user-interaction logging.

---

## Table of Contents

* [Features](#features)
* [Prerequisites](#prerequisites)
* [Project Structure](#project-structure)
* [Usage](#usage)
* [Configuration](#configuration)
* [Logging](#logging)
* [Serialization](#serialization)
* [Sorting Algorithms](#sorting-algorithms)
* [Future Improvements](#future-improvements)

---

## Features

* **Automatic Data Loading**: On startup, attempts to load `library.ser`; falls back to CSV (`books.txt`) if missing.
* **View & Search**: Display all books or locate by title, author, or publication year.
* **Sort Options**:

  * **Title** (Bubble Sort)
  * **Author** (Insertion Sort)
  * **Year** (Quick Sort)
* **Persistence**: Save and load book list using Java serialization.
* **Interaction Logging**: Timestamped logs of all user actions.

---

## Prerequisites

* Java Development Kit (JDK) 8 or higher
* Git (for repository setup)
* Terminal or command prompt

---

## Project Structure

```
├── resources/
│   └── data/
│       ├── books.txt               # CSV dataset: Title,Author,Year
│       ├── library.ser             # Serialized library (auto-generated)
│       └── user_interactions.log   # Append-only log file
├── src/
│   ├── Main.java
│   ├── Book.java
│   ├── Library.java
│   ├── LibraryMenu.java
│   ├── LibrarySerializer.java
│   ├── SortUtil.java
│   └── UserInteractionLogger.java
├── .gitignore
└── README.md
```

## Usage

After launch, use the numbered menu:

```plaintext
=== Main Menu ===
1. View All Books
2. Sort Books by Title
3. Sort Books by Author
4. Sort Books by Year
5. Search for a Book
6. Exit
````

* **View All Books**: Lists every book with title, author, year.
* **Sort**: Choose criterion to reorder the list.
* **Search**: Enter a keyword (partial or full match).
* **Exit**: Saves state, logs action, and closes.

*Example Session:*

```
Enter choice: 5
Enter keyword: Tolkien
Book found: Book{title='The Hobbit', author='J.R.R. Tolkien', publicationYear=1937}
```

---

## Configuration

* **books.txt**: Each line `Title,Author,Year` (e.g., `1984,George Orwell,1949`).
* **Paths**: Data files located under `resources/data/`.
* **Log File**: `resources/data/user_interactions.log`.

---

## Logging

`UserInteractionLogger` writes entries to `user_interactions.log`:

```
2025-07-10T15:30:12 - Viewed all books
2025-07-10T15:32:07 - Search for: "Hobbit"
```

---

## Serialization

Handled by `LibrarySerializer`:

* `saveLibrary(List<Book>, String)`: Serialize book list.
* `loadLibrary(String)`: Deserialize or return `null` if not found.

---

## Sorting Algorithms

| Criterion | Algorithm      | Avg. Complexity |
| --------- | -------------- | --------------- |
| Title     | Bubble Sort    | O(n²)           |
| Author    | Insertion Sort | O(n²)           |
| Year      | Quick Sort     | O(n log n)      |

---

## Future Improvements

* Add interactive **CRUD** (create/update/delete).
* Develop a **GUI** (Swing/JavaFX).
* Support **database** integration (SQL/NoSQL).
* Enhance **search** (multi-criteria, partial matching).
* Enable **export** (JSON, XML, CSV).
  
