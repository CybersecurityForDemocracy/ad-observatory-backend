# Ad Observatory Backend
backend code for Ad Observatory

## Running server locally for development
1. Setup virtualenv `virtualenv venv -p python3.7 && source venv/bin/activate && pip install --upgrade -r requirements.txt`
1. copy `.env.example` to `.env` and fill in correct values for fields with `<PLACEHOLDER>`.
1. start cloud SQL proxy [instructions to install here](https://cloud.google.com/sql/docs/mysql/quickstart-proxy-test) so that local server can connect to dev database
example cloud SQL proxy command: `./cloud_sql_proxy --instances=<instance name>=tcp:<port for local forwarding>`
1. set `FB_ADS_DATABASE_PORT` and `GOOGLE_ADS_DATABASE_PORT` in `.env` to `<port for local forwarding>` specified in `cloud_sql_proxy` command (prior step)
1. start server: `python -m main` OR to run similar to production: `gunicorn -c gunicorn.conf.py -b :5000 main:app`

Above command starts server listening on port 5000, and should be accessible at `http://localhost:5000/`

## Deploying to app engine
`gcloud app deploy --project=<project ID> <app name>.yaml`
