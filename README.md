# Description
A PoC with bokeh server with a custom basic login view

## STEPS

- **STEP01**: clone the template auth bokeh repository as project name alias

```
$ git clone https://gsdpi@dev.azure.com/gsdpi/avib/_git/uniovi-gsdpi-bokeh-template uniovi-gsdpi-bokeh-mp-traccion
```

- **STEP02**: Create project and activate it

If you want download the modules from scratch

```
$ python3 -m venv .venv
$ source .venv/bin/activate
```

- **STEP02**: Install default python modules in your project

```
(.venv)$ pip install -r requirements.txt
```

- **STEP02**: Configure Application arguments

Edit bootstrap Bokeh Server default arguments

```
app = "uniovi-gsdpi-bokeh-template"               --> App main folder bokeh application (must b ethe same as main folder)
app_prefix = "prefix"                             --> Prefix for your bokeh application
app_port = 5006                                   --> Port for your bokeh application
app_title = "Bokeh Template"                      --> Title for your bokeh application
app_logo = "logo_gsdpi.png"                       --> Logo for your bokeh application
app_background = "login_background.png"           --> Background for your bokeh application
cookie_secret = "my super secret"                 --> Cookie secret for your bokeh application
websocket_origin = ["localhost:" + str(app_port)] --> Web Origins Domains for your bokeh application
basic_username = "bokeh"                          --> Username credentials for your bokeh application
basic_password = "bokeh"                          --> Password credentials for your bokeh application
login_level = logging.DEBUG                       --> Logging level or your bokeh application
```

- **STEP03**: Execute application and debug

```
(.venv)$ python boostrap.py
```

- **STEP04**: Build the docker image

Exec this command to build:

```
(.venv)$ deactivate
$ docker build -t uniovi-gsdpi-bokeh-template:1.0.0 .
```

- **STEP05**: run the docker container

Exec this command to run the container:

```
$ docker run --rm --name uniovi-gsdpi-bokeh-template -p 5006:5006 uniovi-gsdpi-bokeh-template:1.0.0
```

- **STEP06**: tag image docker image to be uploaded to azure container registry

```
$ docker tag uniovi-gsdpi-bokeh-template:1.0.0 avibdocker.azurecr.io/uniovi-gsdpi-bokeh-template:1.0.0
```

- **STEP07**: push image docker image

```
$ docker push avibdocker.azurecr.io/uniovi-gsdpi-bokeh-template:1.0.0
```