<div align="center">
<h3><code>whodat</code></h3>
<br/>
Quickly get IP, Prefix, and ASN Information at the command-line.
<br/>
<br/>
<a href="https://github.com/thatmattlove/whodat/actions?query=workflow%3ATest">
  <img alt="GitHub Workflow Status" src="https://img.shields.io/github/workflow/status/thatmattlove/whodat/Test?style=for-the-badge">
</a>
</div>

## Usage

### Download the latest [release](https://github.com/thatmattlove/whodat/releases/latest)

There are multiple builds of the release, for different CPU architectures/platforms:

There are multiple builds of the release, for different CPU architectures/platforms. Download and unpack the release for your platform:

```shell
wget <release url>
tar xvfz <release file> whodat
```

### Run the binary

```console
$ ./whodat --help

whodat
  Quickly get IP, Prefix, and ASN Information at the command-line.

Options:

  -h, --help               Show this Help Menu
  -p, --prefixes[=false]   Get ASN's Advertised Prefixes
```

### IP Lookup

To query a single host IP, simply:

```bash
whodat 1.1.1.1

  1.1.1.1 (one.one.one.one)

    APNIC and Cloudflare DNS Resolver project
    AS13335

    Prefix: 1.1.1.0/24 (APNIC-LABS)
    Allocation: 1.1.1.0/24
    RIR: APNIC
```

### Prefix Lookup

To query a prefix:

```bash
whodat 1.1.1.0/24

  1.1.1.0/24 (APNIC-LABS)

    APNIC and Cloudflare DNS Resolver project

    Origins:
      13335 (Cloudflare, Inc.)

    Allocation: 1.1.1.0/24
    RIR: APNIC
```

### ASN Lookup

To query an ASN:

```bash
whodat AS13335 # or whodat 13335

  13335 (Cloudflare, Inc.)

    Website: https://www.cloudflare.com
```

You can also add the `-p` flag to get all of the ASN's originated prefixes, courtesy of [bgpstuff.net](https://bgpstuff.net) by @mellowdrifter:

```bash
whodat AS13335 -p

  13335 (Cloudflare, Inc.)

    Website: https://www.cloudflare.com
    Prefixes:
      IPv4:
        1.0.0.0/24
        1.1.1.0/24
        103.21.244.0/24
        ...
      IPv6:
        2400:cb00:100::/48
        2400:cb00:102::/48
        2400:cb00:103::/48
        ...

```

## About `whodat` & Credits

`whodat` is nothing more than a wrapper around services other people have created. `whodat` fetches data from the following sources:

- [bgp.tools](https://bgp.tools)
- [bgpstuff.net](https://bgpstuff.net)
- [RIPEStat](https://stat.ripe.net)
- [PeeringDB](https://peeringdb.com)
- [Cloudflare](https://cloudflare.com)

Most of the data is fetched from a serverless function (see [`whodat` server](https://github.com/thatmattlove/whodat-server)), which is what does the actual querying of each of the above resources. The data is cached at the server level to reduce load on those services and improve response times.

[![GitHub](https://img.shields.io/github/license/thatmattlove/whodat?color=000000&style=for-the-badge)](https://github.com/thatmattlove/whodat/blob/main/LICENSE)
