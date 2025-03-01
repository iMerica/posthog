![PostHog header](https://posthog-static-files.s3.us-east-2.amazonaws.com/Website-Assets/github-cover.png)

# PostHog (Community Edition)

PostHog is open source product analytics, built for developers. Automate the collection of every event on your website or app, with no need to send data to 3rd parties. It's a 1 click to deploy on your own infrastructure, with full API/SQL access to the underlying data.

## Quick start

1-click Heroku deploy:

<a href="https://heroku.com/deploy?template=https://github.com/posthog/posthog"><img src="https://www.herokucdn.com/deploy/button.svg" width="250px" /></a>


See [PostHog docs](https://github.com/PostHog/posthog/wiki) for in-depth walk throughs on functionality.

![PostHog dashboard screenshot](https://posthog.com/wp-content/uploads/2020/02/Screenshot-2020-02-13-at-23.14.36-2.png)

Join the [PostHog Users Slack](https://join.slack.com/t/posthogusers/shared_invite/enQtOTUwNjU1ODc1MjQ5LTU5ZDhlYTRiYmUyMDAxNDZjNzk4MDEwNzZkNTQ2YzMxMjVjY2EzYmIzZjllN2YwYmExODI5M2I3NGNiODFhZmU) if you need help, want to chat, or are thinking of a new feature idea.

## Features

- **Event-based** analytics at a user level - see which users are doing what in your application.
- **Complete control** over your data - host it yourself.
- **Automatically capture** clicks and page views to do analyze what your users are doing **retroactively**. 
- Libraries for **[JS](https://github.com/PostHog/posthog/wiki/JS-integration), [Python](https://github.com/PostHog/posthog/wiki/python-integration), [Ruby](https://github.com/PostHog/posthog/wiki/ruby-integration), [Node](https://github.com/PostHog/posthog/wiki/node-integration)** + API for anything else.
- Beautiful **graphs, funnels and dashboards**.
- Super easy deploy using **Docker** or **Heroku**.

## Event autocapture

<img src="https://posthog-static-files.s3.us-east-2.amazonaws.com/Website-Assets/Creating+new+action+with+toolbar.gif" width="100%">

## Philosophy

Many engineers find it painful to work out how their products are being used. This makes design decisions tough. PostHog solves that.

We also strongly believe 3rd party analytics don't work anymore in a world of Cookie laws, GDPR, CCPA and lots of other 4 letter acronyms. There should be an alternative to sending all of your users' personal information and usage data to 3rd parties.

PostHog gives you full control over all your users' data, while letting anyone easily perform powerful analytics.

It means you can know who is using your app, how they're using, and where you lose users in the sign up process.

## What's cool about this?

PostHog is the only <strong>product-focused</strong> open source analytics library, with an event and user-driven architecture. That means tracking identifiable (where applicable) user behavior, and creating user profiles. We are an open source alternative to Mixpanel, Amplitude or Heap, designed to be more developer friendly.

There are a couple of session-based open source libraries that are nice alternatives to Google Analytics. That's not what we are focused on.

## One-line docker preview

```bash
docker run -t -i --rm --publish 8000:8000 -v postgres:/var/lib/postgresql posthog/posthog:preview
```

This image has everything you need to try out PostHog locally! It will set up a server on http://127.0.0.1:8000.

## Deploy to Heroku

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/posthog/posthog)

## Production installation

The preview image has Postgres running locally and runs in debug mode.

For a production installation you have a few options:

### Deploy to Heroku

Heroku is the quickest way to get a production PostHog environment up-and-running.

We recommend getting at the very least a `hobby-dev` Postgres and Dyno for low volumes of events.

### Docker

Using the [posthog/posthog:latest](https://hub.docker.com/r/posthog/posthog) Docker image. You'll need to spin up a separate Postgres docker container. We've included a docker-compose.yml file that does that.

[Click here](https://github.com/PostHog/posthog/wiki/Upgrading-PostHog) for instructions on upgrading PostHog on Heroku to the latest version.

**On Ubuntu**

1. [Install Docker](https://docs.docker.com/installation/ubuntulinux/)
2. [Install Docker Compose](https://docs.docker.com/compose/install/)
3. Run the following:
```bash
sudo apt-get install git
git clone https://github.com/posthog/posthog.git
cd posthog
docker-compose build
docker-compose up -d
```

### From source
1. Make sure you have Python >= 3.7 and pip installed
2. [Install Yarn](https://classic.yarnpkg.com/en/docs/install/#mac-stable)
3. Run the following:
```bash
git clone https://github.com/posthog/posthog.git
yarn build
pip install -r requirements.txt
gunicorn posthog.wsgi --config gunicorn.config.py --log-file -
```

### Running behind a proxy?
See [running behind a proxy](https://github.com/PostHog/posthog/wiki/Running-behind-a-proxy)

## Development
### Running backend (Django)
1) Make sure you have python 3 installed `python3 --version`
2) Make sure you have postgres installed `brew install postgres`
3) Start postgres, run `brew services start postgresql`
4) Create Database `createdb posthog`
5) Navigate into the correct folder `cd posthog`
6) Run `python3 -m venv env` (creates virtual environment in current direction called 'env')
7) Run `source env/bin/activate` (activates virtual environment)
8) Run `pip install -r requirements.txt`. If you have problems with this step (TLS/SSL error), then run `~ brew update && brew upgrade` followed by `python3 -m pip install --upgrade pip`, then retry the requirements.txt install.
9) Run migrations `python manage.py migrate`
10) Run `DEBUG=1 python manage.py runserver`
11) Run the tests and frontend

### Running backend tests
`bin/tests`

### Running frontend (React)

If at any point, you get "command not found: nvm", you need to install nvm, then use that to install node.

1) Make sure you are running Django above in a separate terminal
2) Now run `bin/start-frontend`
3) Optional: If you're making changes to the editor, you'll need to do `cd frontend && yarn start-editor` to watch changes.

## Open source / Paid

This repo is entirely MIT licensed. We charge for things like teams, permissioning, data lake integrations, and support. Please email hey@posthog.com and we will gladly help with your implementation.

## Contributors 🦸
[//]: contributor-faces
<a href="https://github.com/ellmh"><img src="https://avatars1.githubusercontent.com/u/53315310?v=4" title="ellmh" width="80" height="80"></a>
<a href="https://github.com/mrkurt"><img src="https://avatars1.githubusercontent.com/u/7724?v=4" title="mrkurt" width="80" height="80"></a>
<a href="https://github.com/rberrelleza"><img src="https://avatars0.githubusercontent.com/u/475313?v=4" title="rberrelleza" width="80" height="80"></a>
<a href="https://github.com/mariusandra"><img src="https://avatars0.githubusercontent.com/u/53387?v=4" title="rberrelleza" width="80" height="80"></a>
<a href="https://github.com/timgl"><img src="https://avatars1.githubusercontent.com/u/1727427?v=4" title="timgl" width="80" height="80"></a>
<a href="https://github.com/jamesefhawkins"><img src="https://avatars3.githubusercontent.com/u/47497682?v=4" title="jamesefhawkins" width="80" height="80"></a>
<a href="https://github.com/Tannergoods"><img src="https://avatars1.githubusercontent.com/u/60791437?v=4" title="Tannergoods" width="80" height="80"></a>

[//]: contributor-faces
