# dokku-letsencrypt

dokku-letsencrypt is a plugin for [dokku][dokku] that gives the ability to request and install automatically certificates from [Let’s Encrypt][letsencrypt].

## Installation

```sh
$ dokku plugin:install https://github.com/dokku/dokku-letsencrypt.git
```

## Commands

```
$ dokku help
    letsencrypt:request <app> <domain> [domain [domain [...]]]        Request one or more domain(s) for <app> from Let’s Encrypt
```

## Usage

**WARNING: when requesting a certificate, the app has to be deployed and reachable from the internet.**

Request and install a certificate from Let’s Encrypt for `sub.example.com`.
```
$ dokku letsencrypt:request my-app sub.example.com
```

You can request a certificate for multiple domains, just be aware that your app should be linked to those domains since Let’s Encrypt will request a challenge for each one of them.

```
# For example, if we want sub.example.com and example.com we could achieve this
# like that:
$ dokku domains:add my-app example.com
$ dokku domains:add my-app sub.example.com
$ dokku letsencrypt:request my-app sub.example.com example.com
```

## License

This plugin is released under the MIT license. See the file [LICENSE](LICENSE).

[dokku]: https://github.com/dokku/dokku
[letsencrypt]: https://letsencrypt.org/
