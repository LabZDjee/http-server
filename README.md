# *http-server*: a Command-line HTTP Server

It's a fork from [http-party/http-server](https://github.com/http-party/http-server)

Main purpose is to make a standalone executable binary CLI corresponding to `bin/http-server` JS

This executable is build with NPM [pkg](https://www.npmjs.com/package/pkg) utility, stored in a directory called `pkg-binaries` (to be ignored by GIT, syntax then being `pkg . --out-path pkg-binaries`)

Library (`lib/http-server.js`) is left untouched (though a little bit modernized and beautified)

For testing, `pretest` script using outdated `devDependencies` package `common-style` has been removed as code is intended to be beautified, conformed, and linted with Visual Studio Code plug-ins (moreover `common-style` and its replacement [`eslint-config-populist`](https://preview.npmjs.com/package/eslint-config-populist) conflict with the Beautify plug-in in their design rules)

CLI source in `bin/http-server` has been slightly tweaked to suits our needs: having default HTML root directory named `htdocs` and default port `5000`. Also, in case no address is given it defaults to `localhost` not all interfaces (which is the case when `0.0.0.0` is provided as an address)

## HTTP Server CLI Options

```
usage: http-server [path] [options]
default path: ./htdocs
options:
  -p --port    Port to use [5000]
  -a           Address to use [ localhost ], use 0.0.0.0 for listening on all local interfaces
  -d           Show directory listings [true]
  -i           Display autoIndex [true]
  -g --gzip    Serve gzip files when possible [false]
  -b --brotli  Serve brotli files when possible [false]
               If both brotli and gzip are enabled, brotli takes precedence
  -e --ext     Default file extension if none supplied [none]
  -s --silent  Suppress log messages from output
  --cors[=headers]   Enable CORS via the "Access-Control-Allow-Origin" header
                     Optionally provide CORS headers list separated by commas
  -o [path]    Open browser window after starting the server
               Optionally provide a URL path to open the browser window to
  -c           Cache time (max-age) in seconds [3600], e.g. -c10 for 10 seconds
               To disable caching, use -c-1
  -t           Connections timeout in seconds [120], e.g. -t60 for 1 minute
               To disable timeout, use -t0
  -U --utc     Use UTC time format in log messages
  --log-ip     Enable logging of the client's IP address

  -P --proxy         Fallback proxy if the request cannot be resolved. e.g.: http://someurl.com

  --username   Username for basic authentication [none]
               Can also be specified with the env variable NODE_HTTP_SERVER_USERNAME
  --password   Password for basic authentication [none]
               Can also be specified with the env variable NODE_HTTP_SERVER_PASSWORD

  -S --ssl     Enable https
  -C --cert    Path to ssl cert file (default: cert.pem)
  -K --key     Path to ssl key file (default: key.pem)

  -r --robots        Respond to /robots.txt [User-agent: *\nDisallow: /]
  --no-dotfiles      Do not show dotfiles
  -h --help          Print this list and exit
  -v --version       Print the version and exit
```

