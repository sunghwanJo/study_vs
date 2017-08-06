**Frontend**

* [Babel](http://babeljs.io) for ES6 and ES7 magic
* [Webpack](http://webpack.github.io) for bundling
* [Webpack Dev Middleware](http://webpack.github.io/docs/webpack-dev-middleware.html)
* [Clean Webpack Plugin](https://github.com/johnagan/clean-webpack-plugin)
* [fetch](https://github.com/github/fetch) A window.fetch JavaScript polyfill
* [style-loader](https://github.com/webpack/style-loader), [sass-loader](https://github.com/jtangelder/sass-loader) and [less-loader](https://github.com/webpack/less-loader) to allow import of stylesheets in plain css, sass and less,
* [font-awesome-webpack](https://github.com/gowravshekar/font-awesome-webpack) to customize FontAwesome
* [bootstrap-loader](https://github.com/shakacode/bootstrap-loader) to customize Bootstrap
* [ESLint](http://eslint.org), [Airbnb Javascript Styleguide](https://github.com/airbnb/javascript), [Airbnb CSS / Sass Styleguide](https://github.com/airbnb/css) to maintain a consistent code style and [eslint-plugin-import](https://github.com/benmosher/eslint-plugin-import) to make sure all imports are correct
* [mocha](https://mochajs.org/) to allow writing unit tests for the project
* [redux-mock-store](https://github.com/arnaudbenard/redux-mock-store) a mock store for your testing your redux async action creators and middleware
* [expect](https://github.com/mjackson/expect) Write better assertions
* [Nock](https://github.com/pgte/nock) HTTP mocking and expectations library
* [istanbul](https://github.com/gotwarlost/istanbul) to generate coverage when running mocha

**Backend**

* [Django](https://www.djangoproject.com/)
* [Django REST framework](http://www.django-rest-framework.org/) Django REST framework is a powerful and flexible toolkit for building Web APIs
* [WhiteNoise](http://whitenoise.evans.io/en/latest/django.html) to serve files efficiently from Django
* [Prospector](http://prospector.landscape.io/en/master/) a complete Python static analysis tool
* [Bandit](https://github.com/openstack/bandit) a security linter from OpenStack Security
* [pytest](http://pytest.org/latest/) a mature full-featured Python testing tool
* [Mock](http://www.voidspace.org.uk/python/mock/) mocking and testing Library
* [Responses](https://github.com/getsentry/responses) a utility for mocking out the Python Requests library


## Readme Notes

* If the command line starts with $, the command should run with user privileges
* If the command line starts with #, the command should run with root privileges


## Retrieve code

* `$ git submodule init`
* `$ git submodule update`
* `$ ./scripts/get_static_validation.sh`


Remember that when you copy this repository for a new project you need to add the scripts external module using:

* `$ git submodule add https://github.com/Seedstars/culture-scripts scripts`

NOTE: This is only needed in case you copy this code to a new project. If you only clone or fork the repository, the submodule is already configured


## Installation

### Main Project

We use Docker as a development environment. For production, we leave you to set it up the way you feel better,
although it is trivial to extrapolate a production environment from the current docker-compose.yml.
* Install [Docker](https://www.docker.com/products/overview) and [Docker Compose](https://docs.docker.com/compose/install/).
* `$ docker-compose build`


## Running

Run Docker development server

* `$ docker-compose up`

### Accessing a container

You can access shell in a container

* `$ docker exec -i -t <CONTAINER_NAME_OR_ID> /bin/bash`

E.g.

* `$ docker ps  # get the name from the list of running containers`
* `$ docker exec -i -t djangoreactreduxbase_frontend_1 /bin/bash`

### Accessing the database

The database can be accessed @localhost:5433

* `$ psql -h localhost -p 5433 -U vsdbmanager vsdbmanager_dev`


## Testing

To make sure the code respects all coding guidelines you should run the statics analysis and test scripts before pushing any code.

Frontend (javascript tests)

* `$ ./scripts/test_local_frontend.sh`

Backend (django/python tests)

* `$ docker exec -i -t djangoreactreduxbase_backend_1 /bin/bash scripts/test_local_backend.sh`

### Static analysis


Frontend (javascript static analysis)

* `$ ./scripts/static_validate_frontend.sh`

Backend (django/python static analysis)

* `$ docker exec -i -t djangoreactreduxbase_backend_1 /bin/bash scripts/static_validate_backend.sh`

## Gotchas

* This project uses NodeJS v6.x (stable) and the corresponding version of npm
* The npm development server takes longer than the django server to start, as it has to install the npm dependencies (if not already installed) and fire webpack. This means that after the django server starts, you should wait that webpack finishes compiling the .js files.
* If your IDE has builtin language support for python with auto-imports (e.g. PyCharm), you can create a virtualenv and install the py-requirements.
* If you are annoyed by docker creating files belonging to root (which is Docker's intended behaviour), you can run `# chown -hR $(whoami) .` before firing up the server.
* While testing the backend, if you have a local virtualenv, you can run the static validation without running a docker container.
* While testing the backend, if you have a local virtualenv and a local database configured with the dev settings, you can run the tests without running a docker container.


## Contributing

We welcome contributions from the community, given that they respect these basic guidelines:

* All Tests & Static Analysis passing;
* 100% code coverage;

If you want to tackle any open issue, well..... Just go for it! :)
