# Set up the bug report

1. start Strapi and add some data
2. make a screenshot of the data in Strapi admin
3. make a screenshot of the data in `psql`
4. export Postgres database (with Postgres tools (`pg_dump`))
   With running containers, do this:
   `docker exec strapi-export-bug-00_postgres pg_dump -U postgres app > ./backups/pg_before.sql`
5. stop the Strapi containers and run `docker compose run strapi npm run strapi export -- --no-encrypt --no-compress -f /usr/src/app/backups/<export filename>`; make a screenshot of the output
6. make a screenshot of Strapi signup page and of empty collections in Strapi admin
7. make a screenshot of the data in `psql`, showing empty tables
8. then, perhaps, export the Postgres database again

Add

- the project code
- the Postgres db before and after backup
- the Strapi backup
