## Testing Notes
### Testing with tox

Test with tox by running the following as used in the GitHub Actions Workflows:

```
poetry run tox -e py
```

### Setting up a SQL Server image

1. Set up a SQL Server image by running the command used in the `tox.ini` file:

```
docker run -p 1433:1433 -e "MSSQL_SA_PASSWORD=testDatabase1" -e "ACCEPT_EULA=Y" mcr.microsoft.com/mssql/server:2019
```

2. Selectively test using the `-k` option in pytest:

```
poetry run pytest -v -k TestCurrent
```