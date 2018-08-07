{{ cookiecutter.project_name }}
==============================

__Version:__ {{ cookiecutter.version }}

{{ cookiecutter.project_description }}

## Getting up and running

**Install Minimum requirements:**
* [pip][install-pip]
* [postgres][install-postgres]{% if cookiecutter.postgis == 'y' %} with postgis{% endif %}
* [fabric][fab]
* [python(version=3.x)][python3-docs]

{% if cookiecutter.add_celery == 'y' %}* [Celery][install-celery]{% endif %}

{% if cookiecutter.add_celery.lower() == 'y' %}* [redis][install-redis]{% endif %}


On Mac OSX:

```
brew install postgres python3
[sudo] pip install fabric
```

On Ubuntu:

```
[sudo] apt-get update
[sudo] apt-get install postgresql postgresql-contrib python3
[sudo] pip install fabric3
```

[install-postgres]: https://www.postgresql.org/docs/current/static/install-short.html

[python3-docs]: https://docs.python.org/3/

[fab]: http://www.fabfile.org/installing.html

[install-pip]: https://pip.pypa.io/en/stable/installing/

[install-celery]: http://www.celeryproject.org/install/

[install-redis]: https://redis.io/topics/quickstart

In your terminal, type or copy-paste the following:

    git clone git@github.com:{{ cookiecutter.github_username }}/{{ cookiecutter.github_repository }}.git; cd {{ cookiecutter.github_repository }}; fab init

Go grab a cup of coffee, we bake your hot development machine.

Useful commands:

- `fab serve` - start [django server](http://localhost:8000/)
- `fab deploy_docs` - deploy docs to server
- `fab test` - run the test locally with ipdb

**NOTE:** Checkout `fabfile.py` for all the options available and what/how they do it.


## Deploying Project

The deployment are managed via travis, but for the first time you'll need to set the configuration values on each of the server.

Check out detailed server setup instruction [here](docs/backend/server_config.md).

## How to release {{ cookiecutter.project_name }}

Execute the following commands:

```
git checkout master
fab test
bumpversion patch  # 'patch' can be replaced with 'minor' or 'major'
git push origin master
git push origin master --tags
git checkout qa
git rebase master
git push origin qa
```

## Contributing

Golden Rule:

> Anything in **master** is always **deployable**.

Avoid working on `master` branch, create a new branch with meaningful name, send pull request asap. Be vocal!

Refer to [CONTRIBUTING.md][contributing]

[contributing]: http://github.com/{{cookiecutter.github_username}}/{{cookiecutter.github_repository}}/tree/master/CONTRIBUTING.md
