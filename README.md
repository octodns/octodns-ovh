## OVHcloud DNS v6 API provider for octoDNS

An [octoDNS](https://github.com/octodns/octodns/) provider that targets [OVHcloud DNS](https://www.ovhcloud.com/en/domains/dns-subdomain/).

### Installation

#### Command line

```
pip install octodns-ovh
```

#### requirements.txt/setup.py

Pinning specific versions or SHAs is recommended to avoid unplanned upgrades.

##### Versions

```
# Start with the latest versions and don't just copy what's here
octodns==0.9.14
octodns-ovh==0.0.1
```

##### SHAs

```
# Start with the latest/specific versions and don't just copy what's here
-e git+https://git@github.com/octodns/octodns.git@9da19749e28f68407a1c246dfdf65663cdc1c422#egg=octodns
-e git+https://git@github.com/octodns/octodns-ovh.git@ec9661f8b335241ae4746eea467a8509205e6a30#egg=octodns_ovh
```

### Configuration

```yaml
providers:
  ovh:
    class: octodns_ovh.OvhProvider
    # OVH api v6 endpoint
    endpoint: ovh-eu
    # API application key
    application_key: env/OVH_APPLICATION_KEY
    # API application secret
    application_secret: env/OVH_APPLICATION_SECRET
    # API consumer key
    consumer_key: env/OVH_CONSUMER_KEY
```

### Support Information

#### Records

OvhProvider supports A, AAAA, CAA, CNAME, DKIM, MX, NAPTR, NS, PTR, SPF, SRV, SSHFP, and TXT

#### Dynamic

OvhProvider does not support dynamic records.

### Development

See the [/script/](/script/) directory for some tools to help with the development process. They generally follow the [Script to rule them all](https://github.com/github/scripts-to-rule-them-all) pattern. Most useful is `./script/bootstrap` which will create a venv and install both the runtime and development related requirements. It will also hook up a pre-commit hook that covers most of what's run by CI.
