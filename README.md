# postgres-readonly-user

1. Login to PostgreSQL

```
psql -U postgres -d your_database_name

```
2. Create the Read-Only User
```
CREATE USER readonly_user WITH PASSWORD 'readonly_password';
```
3. Grant CONNECT and USAGE Permissions
```
GRANT CONNECT ON DATABASE your_database_name TO readonly_user;
\c your_database_name  -- Reconnect to apply schema-level permissions

GRANT USAGE ON SCHEMA public TO readonly_user;
```
4. Grant SELECT on Existing Tables
```
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readonly_user;
```
5. Ensure Future Tables Are Also Read-Only
```
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT SELECT ON TABLES TO readonly_user;
```
