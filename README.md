# Django React Notes

A notes application with a Django REST Framework API and a React frontend built with Vite. Users can register, log in, and manage their own notes.

## Requirements

- Python 3.12 or newer
- Node.js and npm
- PostgreSQL

## Backend setup

Open a terminal in the project root and run:

```powershell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Create a PostgreSQL database and user, then add the connection settings to `backend/.env`:

```env
DB_NAME=your_database_name
DB_USER=your_database_user
DB_PWD=your_database_password
DB_HOST=localhost
DB_PORT=5432
```

Replace the example values with the database and credentials you created. Then apply migrations and start Django:

```powershell
python manage.py migrate
python manage.py runserver
```

The API is available at `http://127.0.0.1:8000/`.

## Frontend setup

In another terminal from the project root:

```powershell
cd frontend
npm install
```

Set the API URL in `frontend/.env`:

```env
VITE_API_URL=http://127.0.0.1:8000
```

Start the Vite development server:

```powershell
npm run dev
```

Open the local URL printed by Vite. Keep the Django server running while using the frontend.

## Available frontend scripts

Run these commands from `frontend/`:

```powershell
npm run dev
npm run build
npm run lint
npm run preview
```

## Main API routes

- `POST /api/user/register/` — create an account
- `POST /api/token/` — obtain access and refresh tokens
- `POST /api/token/refresh/` — refresh an access token
- `GET` and `POST /api/notes/` — list or create the authenticated user's notes
- `DELETE /api/notes/delete/<id>/` — delete one of the authenticated user's notes

