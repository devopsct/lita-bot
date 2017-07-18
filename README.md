# DevOps CT Lita Bot

This is the Lita bot that lives in our Slack team.

## Configuration Management

Secrets are managed through [Torus CLI](http://torus.sh).

1. Signup for [Torus](http://torus.sh) if you haven't already
2. Setup and Org and Project for Torus:
  * `torus orgs create <name>`
  * `torus projects create --org <org> <name>`
3. Link to your project: `torus link`
4. Create an environment for Heroku: `torus envs create heroku`
5. Create a Heroku machine role: `torus machines roles create heroku`
6. Give your machine role access: `torus allow rl /<org>/<project>/heroku/default/** heroku`
7. Create a Heroku machine for your deployment: `torus machines create heroku-instance -r heroku`
8. Set the following env vars in Heroku using output from step 7:
  * `TORUS_TOKEN_ID`: Machine Token ID
  * `TORUS_TOKEN_SECRET`: Machine Token Secret
9. Add the following secrets to Torus: `torus set -e heroku <ENV var> <value>`
  * `LITA_SLACK_TOKEN` - `xoxb-YOUR-TOKEN-HERE`
