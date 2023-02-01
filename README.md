# README

## 2023-01-31

Try to work a docker build that take the following entrypoint

From docker-compose

```dockerfile
uvicorn app.main:app --reload --workers 1 --host 0.0.0.0 --port 8000
```

Issue is the the `--workers 1` option is not working

```dockerfile
CMD ["uvicorn", "app.main:app", "--reload", "--host", "0.0.0.0", "--port", "8000"]
```
This is what's working
```dockerfile
CMD ["uvicorn", "app.main:app", "--reload", "--host", "0.0.0.0", "--port", "8000"]
```

```bash
docker run -d --name fast-api-container -p 8004:8000 fast-api-app
```

### Bring Things Up

```bash
docker build -t fast-api-app .
docker run -d --name fast-api-container -p 8004:8000 fast-api-app
curl http://localhost:8004/docs
docker container ls --all
docker container stop fast-api-container
docker container rm fast-api-container
```

