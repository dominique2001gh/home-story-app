# Database Schema

## users
| Column        | Type                   | Notes                     |
|---------------|------------------------|---------------------------|
| id            | SERIAL PRIMARY KEY     |                           |
| name          | VARCHAR(100) NOT NULL  |                           |
| email         | VARCHAR(255) UNIQUE NOT NULL |                   |
| password_hash | TEXT NOT NULL          |                           |
| avatar_url    | TEXT                   |                           |
| bio           | TEXT                   |                           |
| created_at    | TIMESTAMP DEFAULT now()|                           |

## listings
| Column     | Type                   | Notes                     |
|------------|------------------------|---------------------------|
| id         | SERIAL PRIMARY KEY     |                           |
| user_id    | INTEGER NOT NULL       | FK → users(id)            |
| title      | TEXT NOT NULL          |                           |
| address    | TEXT                   |                           |
| price      | NUMERIC(12,2)          |                           |
| status     | VARCHAR(20)            | e.g. “available”          |
| created_at | TIMESTAMP DEFAULT now()|                           |

## stories
| Column       | Type                      | Notes                         |
|--------------|---------------------------|-------------------------------|
| id           | SERIAL PRIMARY KEY        |                               |
| listing_id   | INTEGER NOT NULL          | FK → listings(id)             |
| user_id      | INTEGER NOT NULL          | FK → users(id)                |
| video_url    | TEXT NOT NULL             |                               |
| transcript   | TEXT                      |                               |
| tags         | TEXT[]                    | array of relevant tags        |
| created_at   | TIMESTAMP DEFAULT now()   |                               |

## messages
| Column      | Type                    | Notes                         |
|-------------|-------------------------|-------------------------------|
| id          | SERIAL PRIMARY KEY      |                               |
| sender_id   | INTEGER NOT NULL        | FK → users(id)                |
| listing_id  | INTEGER NOT NULL        | FK → listings(id)             |
| content     | TEXT NOT NULL           |                               |
| timestamp   | TIMESTAMP DEFAULT now() |                               |

## favorites
| Column      | Type                    | Notes                         |
|-------------|-------------------------|-------------------------------|
| id          | SERIAL PRIMARY KEY      |                               |
| user_id     | INTEGER NOT NULL        | FK → users(id)                |
| listing_id  | INTEGER NOT NULL        | FK → listings(id)             |
| created_at  | TIMESTAMP DEFAULT now() |                               |
