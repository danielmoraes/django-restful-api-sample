# Django RESTful Sample Project

This is a sample Django project using the Django RESTful Framework with
JSON Token authentication.

## Setup

At the root directory of this repository, do the following:

### Create a virtual environment and install the dependencies:

```sh
python3 -m virtualenv -p python3 venv
. venv/bin/activate
pip3 install -r drs/requirements.txt
```

### Start the Django development server

```sh
cd drs
./manage.py migrate
./manage.py runserver
```

## Examples

### Login

```sh
USERNAME='admin'
PASSWORD='adminadmin'

curl \
    -X POST \
    -d "username=$USERNAME&password=$PASSWORD" \
    http://localhost:8000/api/auth/
```

### List Users

```sh
TOKEN='eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFkbWluQGRycy5jb20iLCJ1c2VybmFtZSI6ImFkbWluIiwidXNlcl9pZCI6MSwiZXhwIjoxNDkxMTQwNTUzfQ.7_w375_IBFiDTqDN8XK7pdCzQSt_lKyRSud7ceG1g-s'

curl \
    -X GET \
    -H 'Content-Type: application/json' \
    -H "Authorization: JWT $TOKEN" \
    -H 'Accept: application/json; indent=4' \
    http://localhost:8000/api/users/
```
