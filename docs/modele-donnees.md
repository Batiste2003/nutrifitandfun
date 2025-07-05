# Data Model – Nutri Fit & Fun

---

## User (`users`)
- `id`: UUID
- `email`: string
- `password_hash`: string
- `first_name`: string
- `last_name`: string
- `role`: enum ('admin', 'user')
- `photo`: string (URL)
- `signup_date`: datetime
- `last_login`: datetime
- `google_id`: string (optional)
- `apple_id`: string (optional)
- `microsoft_id`: string (optional)

---

## Blog Post (`posts`)
- `id`: UUID
- `title`: string
- `slug`: string
- `content`: text/markdown
- `image`: string (URL)
- `published_at`: datetime
- `author_id`: UUID (foreign key users)
- `categories`: array[string]
- `status`: enum ('draft', 'published')

---

## Comment/Reaction (`comments`)
- `id`: UUID
- `post_id`: UUID (foreign key posts)
- `user_id`: UUID (foreign key users)
- `content`: text
- `created_at`: datetime
- `type`: enum ('comment', 'like', 'emoji')

---

## Booking (`reservations`)
- `id`: UUID
- `user_id`: UUID (foreign key users)
- `coach_id`: UUID (foreign key users, admin)
- `date`: datetime
- `start_time`: time
- `end_time`: time
- `status`: enum ('pending', 'validated', 'refused', 'cancelled')
- `google_event_id`: string (for calendar sync)
- `payment_id`: UUID (foreign key payments)

---

## Payment (`payments`)
- `id`: UUID
- `user_id`: UUID (foreign key users)
- `reservation_id`: UUID (foreign key reservations)
- `amount`: float
- `currency`: string
- `date`: datetime
- `status`: enum ('pending', 'completed', 'refused')
- `stripe_session_id`: string

---

## Message (`messages`)
- `id`: UUID
- `from_id`: UUID (foreign key users)
- `to_id`: UUID (foreign key users)
- `content`: text
- `date`: datetime
- `read`: boolean

---

## Notification (`notifications`)
- `id`: UUID
- `user_id`: UUID (foreign key users)
- `type`: string (e.g. 'booking', 'payment', 'message', 'signup')
- `content`: text
- `date`: datetime
- `read`: boolean

---

## KPI / Coaching Tracking (`kpis`)
- `id`: UUID
- `user_id`: UUID (foreign key users)
- `date`: datetime
- `type`: string (e.g. 'weight', 'BMI', 'goal', etc.)
- `value`: float
- `comment`: text (optional)

---