[![Build Status](https://travis-ci.org/flipdot/drinks-touch.svg?branch=master)](https://travis-ci.org/flipdot/drinks-touch)

# Change 4

Digital replacement for the drinks talsadklaksdkasldlly list featuring a touchscreen, user management and a barcode scanner.

![](https://flipdot.org/wikistatic/common/flipdot.png)

## Table of Content

-   asdasd

    -   asdasd
-   asasds
-   sadasdas
-   asdasd

![](https://pbs.twimg.com/media/EAyZi-KXkAAmk8Z.jpg)

## Development

This project is deployed withiasdasdasdasdn the [drinks-touch_stack](https://github.com/flipdot/drinks-touch_stack/) in accordance to the [DargStack template](https://github.com/Dargmuesli/dargstack-template/) to make deployment a breeze.

The provided `Dockerfile` lets you build a localized Python image. Build it with the following command:

```bash
docker build -t flipdot/drinks-touch .
```

The following information is therefore only useful if you decide to deploy this project containerless.

### Build

This project does not require any build procedure.

### Configuration

The following configuration files are evaluated at execution time and must be derived from their respective examples, which can be found in the same directories.

-   `drinks_touch/config.py`
-   `drinks_touch/acme/config.py`

### Deployment

#### Dependencies

-   LDAP server, reachable via `ldap://rail/` (see [users.py](drinks_touch/users/users.py))
-   PostgreSQL @localhost (see [storage.py](drinks_touch/database/storage.py))
-   touch display with a minimum of 480x800 px.

Install dependencies like this:

```bash
sudo apt-get install libsasl2-dev python-dev libldap2-dev libssl-dev
pip2 install -r requirements.txt
```

Then, start PostgreSQL and OpenLDAP with `systemctl start`. And finally, run the entrypoint script `drinks_touch/game.py`.

For embedded systems it is recommended to use `@reboot runGame.sh` inside a cron tab.
This starts an X server, sets various display properties and puts the application itself in a loop.

## Profiling

To profile the time individual lines of code take to execute install _line_profiler_.

```
pip install line_profiler
```

Then add @profile to the methods you are interested in.

Inside `drinks_touch`, run with

```
kernprof -l game.py
```

And analyze results with

```
python -m line_profiler game.py.lprof | less
```

## License

TODO
