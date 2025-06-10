**Bookstore API Config**


| Variable          | Default                                  | Description                                                      |
|-------------------|------------------------------------------|------------------------------------------------------------------|
| `DATABASE_URL`    | `sqlite:///./books.db`                   | SQLAlchemy database connection string.                           |
| `LOG_LEVEL`       | `INFO`                                   | Root logger level (e.g. DEBUG, INFO, WARNING).                  |
| `LOG_FORMAT`      | `%(levelname)s:%(name)s:%(message)s`     | Python `logging` format string.                                  |
| `PAGE_SIZE`       | `10`                                     | Number of items per page on the `/books/` endpoint.             |
| `APP_ENV`         | `dev`                                    | App environment label (e.g. dev / staging / prod).              |
| `HOST`            | `0.0.0.0`                                | Uvicorn host binding.                                           |
| `PORT`            | `8080`                                   | Uvicorn port.                                                   |
| `RELOAD`          | `False`                                  | Whether Uvicorn runs in reload mode (`True`/`False`).           |
| `ALLOWED_ORIGINS` | `*`                                      | Comma-separated list for CORS allowed origins (`*` = all).      |
| `DB_POOL_SIZE`    | `5`                                      | SQLAlchemy connection-pool size.                                |
| `DB_MAX_OVERFLOW` | `10`                                     | SQLAlchemy max overflow connections beyond the pool size.       |

**DOCKER**
1. Ensure that docker-desktop / docker engine is installed on local environment
2. Open a terminal and set working directory to project directory
    - docker build -t bookstore-api-image .
    - docker run --name bookstore-container -p 8080:8080 bookstore-api-image
    - Quick Test with GET localhost:8080/ ->
    {
    "message": "Welcome to the Books API!"
    }
