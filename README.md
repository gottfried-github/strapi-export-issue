# Reproduce the issue

1. start the containers: `docker compose -f docker-compose.dev.yml up`
2. sign up to Strapi admin (`localhost:1337/admin`) and create some content
3. stop the containers
4. run `docker compose run strapi npm run strapi export -- --no-encrypt --no-compress -f /usr/src/app/backups/<export filename>`
5. start the containers again: `docker compose -f docker-compose.dev.yml up`
6. visit `localhost:1337/admin` and observer that Strapi redirects to sign up page
7. sign up and observe that there's no content

## Accessing database

### Via `psql`

`docker exec -it strapi-postgres_postgres psql -U postgres app`

To see all the Strapi tables in `psql`:

`\dt`

To see details about a specific table:

`\d+ <table name>`

If table name is capitalized, then you should wrap it in double quotes:

`\d+ "Pieces"`

### Via `pgAdmin`

Go to `localhost:5050`

Enter email and password from the compose file service env variables.

## Accessing Strapi

Go to `localhost:1337`.

# 🚀 Getting started with Strapi

Strapi comes with a full featured [Command Line Interface](https://docs.strapi.io/dev-docs/cli) (CLI) which lets you scaffold and manage your project in seconds.

### `develop`

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-develop)

```
npm run develop
# or
yarn develop
```

### `start`

Start your Strapi application with autoReload disabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-start)

```
npm run start
# or
yarn start
```

### `build`

Build your admin panel. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-build)

```
npm run build
# or
yarn build
```

## ⚙️ Deployment

Strapi gives you many possible deployment options for your project including [Strapi Cloud](https://cloud.strapi.io). Browse the [deployment section of the documentation](https://docs.strapi.io/dev-docs/deployment) to find the best solution for your use case.

```
yarn strapi deploy
```

## 📚 Learn more

- [Resource center](https://strapi.io/resource-center) - Strapi resource center.
- [Strapi documentation](https://docs.strapi.io) - Official Strapi documentation.
- [Strapi tutorials](https://strapi.io/tutorials) - List of tutorials made by the core team and the community.
- [Strapi blog](https://strapi.io/blog) - Official Strapi blog containing articles made by the Strapi team and the community.
- [Changelog](https://strapi.io/changelog) - Find out about the Strapi product updates, new features and general improvements.

Feel free to check out the [Strapi GitHub repository](https://github.com/strapi/strapi). Your feedback and contributions are welcome!

## ✨ Community

- [Discord](https://discord.strapi.io) - Come chat with the Strapi community including the core team.
- [Forum](https://forum.strapi.io/) - Place to discuss, ask questions and find answers, show your Strapi project and get feedback or just talk with other Community members.
- [Awesome Strapi](https://github.com/strapi/awesome-strapi) - A curated list of awesome things related to Strapi.

---

<sub>🤫 Psst! [Strapi is hiring](https://strapi.io/careers).</sub>

# Refs

1. https://docs.strapi.io/cms/quick-start#step-4-set-roles--permissions
2. https://docs.strapi.io/cms/api/rest/populate-select#population
3. https://docs.strapi.io/cms/data-management/export
4. https://docs.strapi.io/cms/cli#strapi-export
5. https://docs.strapi.io/cms/api/rest/populate-select#populate-with-filtering
6. https://stackoverflow.com/questions/8333920/passing-a-url-with-brackets-to-curl
7. https://docs.strapi.io/cms/api/rest/populate-select#combining-population-with-other-operators
