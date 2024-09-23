# EspoCRM Training

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## Development

### Getting Started

#### With Python

- Install a [Python virtual environment](https://realpython.com/python-virtual-environments-a-primer/) (On Linux/macOS):

  ```sh
  python3 -m venv venv
  source venv/bin/activate
  ```

- Install dependencies

  ```sh
  pip install -r requirements.txt
  ```

- Build the documentation

  ```sh
  mkdocs serve
  ```

- Preview at: <http://localhost:8000>

#### With Docker

- Install Docker: <https://docs.docker.com/get-docker/>

- Open a terminal at this folder to build a Docker-container:

  ```sh
  docker build --tag data-service-catalogue .
  ```

- Run the Docker-container:

  ```sh
  docker run --rm -it -p 8000:8000 -v ${PWD}:/docs data-service-catalogue
  ```

### Tools in use

- Material for MkDocs: <https://squidfunk.github.io/mkdocs-material/>
