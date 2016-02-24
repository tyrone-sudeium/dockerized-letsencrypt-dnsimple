## Dockerized Let's Encrypt DNSimple

[Docker] image that uses the [Let's Encrypt] Certificate Authority to generate free SSL certificates for domains hosted on- or managed by [DNSimple].

This [Docker] image wraps around [dpiddy/letsencrypt-dnsimple]. 


#### Requirements

- One or more domains hosted- or managed by [DNSimple]
- A machine with [Docker] installed


#### Usage

Assuming you have [Docker] installed on your machine:

```sh
$ docker run --rm \
  -e DNSIMPLE_API_USER=me@example.com \
  -e DNSIMPLE_API_TOKEN=... \
  -e NAMES=example.com,www/example.com \
  -e ACME_CONTACT=mailto:me@example.com \
  -v $(pwd)/live:/cwd/live \
  -ti meskyanichi/letsencrypt-dnsimple
```

*Use `/` instead of `.` to denote the separation between subdomain and [DNSimple] domain.*

If no issues occur, the following files will be created in the `./live` subfolder of the current working directory:

- `example.com_www.example.com-cert.pem`
- `example.com_www.example.com-chain.pem`
- `example.com_www.example.com-fullchain.pem`
- `example.com_www.example.com-key.pem`


#### Author / License

Released under the [MIT License] by [Michael van Rooijen].


[Let's Encrypt]: https://letsencrypt.org/
[DNSimple]: https://dnsimple.com/
[Docker]: https://www.docker.com/
[dpiddy/letsencrypt-dnsimple]: https://github.com/dpiddy/letsencrypt-dnsimple
[MIT License]: https://github.com/meskyanichi/dockerized-letsencrypt-dnsimple/blob/master/LICENSE
[Michael van Rooijen]: https://twitter.com/meskyanichi
