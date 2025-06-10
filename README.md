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
    - docker build -t bookstore-api-image .  **OR** docker pull eythan0106/bookstore-api-image
    - docker run --name bookstore-container -p 8080:8080 bookstore-api-image
    - Quick Test with GET localhost:8080/ ->
    {
    "message": "Welcome to the Books API!"
    }



**K8s / Helm Charts**
1. Enable K8s in Docker on local environment
2. Open a terminal and set working directory to project directory
3. Run Following Commands

helm install bookstore-api-chart-release bookstore-api-chart

**WINDOWS**
### Get the pod name (One Liner)
$POD_NAME = kubectl get pods --namespace default -l "app.kubernetes.io/name=bookstore-api-chart,app.kubernetes.io/instance=bookstore-api-chart-release" -o jsonpath="{.items[0].metadata.name}"

### Get the container port

$CONTAINER_PORT = kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}"

### Port forward

kubectl --namespace default port-forward $POD_NAME 8080:$CONTAINER_PORT

- Quick Test with GET localhost:8080/ ->
    {
    "message": "Welcome to the Books API!"
    }
