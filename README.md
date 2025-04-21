# How To Deploy **EverShop** (for Free)

I created this method since i tried to develop EverShop in AWS free tier, and the machine simply didnt had enough power to build the App

### ! **Disclaimer**: This method is Unsafe for actual selling, The App's Database data and Admin login are too common !

```sql
CREATE USER evershop WITH PASSWORD 'evershop';
```

```sql
CREATE DATABASE evershop;
```

```sql
GRANT ALL PRIVILEGES ON DATABASE evershop TO evershop;
```

```sql
ALTER DATABASE evershop OWNER TO evershop;
```
