## Getting Started with SmoothSail

There are two ways developers can get started with SmoothSail:

- [Docker](#1-setting-up-smoothsail): The easiest, and quickest, way to get up and running with SmoothSail is to to use Docker. This will run each piece of SmoothSail's architecture with limited configuration.
- Run locally: For developers who want complete control and customization they can run each component locally. Each SmoothSail component's GitHub repo is available with documentation to get up and running.
  - [Manager Platform](https://github.com/smooth-sail/smoothsail-manager)
  - [SDK Service](https://github.com/smooth-sail/smoothsail-sdk-service)

### 1. Setting Up SmoothSail

To get started with SmoothSail, you need [`git`](https://git-scm.com/) and [`docker`](https://www.docker.com/) installed on your machine.

Run the following commands:

```bash
git clone https://github.com/smooth-sail/smoothsail.git
cd smoothsail
```

Next, configure your `.env` file.

In order to secure your feature flag API you'll need to provide a 32 character secret key. This should be added to the `.env` file for the `SECRET_KEY` value.

```
SECRET_KEY=<YOUR_SECRET>
```

Execute the following command in order to start the application:

```bash
docker compose up
```

Then open your browser at `http://localhost:3000` to access the SmoothSail feature flag dashboard. You can find your SDK key by going to the SDK Key page.

### 2. Connect your SDK

Find the SDK for your preferred language and import it into your project.

In order to get your SDK running, you'll need two values:

- SDK Service URL: `http://localhost:3001/api/ff-updates-stream`
- SDK Key: `your generated SDK key`

If you made any additional modifications to the `.env` file your configuration details will most likely be different.

### Check a feature toggle

Checking the state of a feature toggle in your code is easy. The syntax will vary depending on your language, but all you need to do is a simple function call to check whether a flag is available. Here's an example in JavaScript:

```javascript
if (client.evaluateFlag("flag-1")) {
  // use new feature
} else {
  // use old feature
}
```

### Custom Configuration with Docker

If you'd like different ports exposed for the Manager Platform, SDK Service, NATS, or Postgres you can modify the values in the `.env` file. Note, you'll have to update the SDK Service address in order to connect your SDK. Postgres details can also be modified in the `.env`.
