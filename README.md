# ee-acme-sh

Bash-Skript zur Installation von Let's Encrypt SSL-Zertifikaten automatisch mit acme.sh auf Servern, die mit EasyEngine laufen.

- [GitHub](https://github.com/VirtuBox/ee-acme-sh)

## Features

- Automatisierte Installation von Let's Encrypt SSL-Zertifikaten über [acme.sh](http://acme.sh)
- Acme-Validierung mit Standalone-Modus oder Cloudflare DNS API
- Unterstützung für Domain, Subdomain & Wildcard SSL-Zertifikate
- IPv6-Unterstützung
- Generieren von ECDSA-Zertifikaten mit dem privaten Schlüssel ECC 384 Bits
- Automatisierte Zertifikatsverlängerung
- Nginx Mainline & stabiler Release-Unterstützung
- Nur Cert-Only-Modus verfügbar

## Installation

```bash
bash <(wget -qO - https://raw.githubusercontent.com/VirtuBox/ee-acme-sh/master/install.sh)

# enable acme.sh & ee-acme-sh
source .bashrc
```

## Update script

Führen Sie einfach den Installationsbefehl erneut aus.

## Verwendung

```bash
Usage: ee-acme [type] <domain> [mode]
  Types:
       -d, --domain <domain_name> ..... for domain.tld + www.domain.tld
       -s, --subdomain <subdomain_name> ....... for sub.domain.tld
       -w, --wildcard <domain_name> ..... for domain.tld + *.domain.tld
  Modes:
       --standalone ..... acme challenge in standalone mode
       --cf ..... acme challenge in dns mode with Cloudflare
  Options:
       --cert-only ... do not change nginx configuration, only display it
       --admin ... secure easyengine backend with the certificate
       -h, --help, help ... displays this help information
Examples:

domain.tld + www.domain.tld in standalone mode :
    ee-acme -d domain.tld --standalone

sub.domain.tld in dns mode with Cloudflare :
    ee-acme -s sub.domain.tld --cf

wildcard certificate for domain.tld in dns mode with Cloudflare :
    ee-acme -w domain.tld --cf

domain.tld + www.domain.tld in standalone mode without editing Nginx configuration :
    ee-acme -d domain.tld --standalone --cert-only

sub.domain.tld in standalone mode to secure easyengine backend on port 22222 :
    ee-acme -s sub.domain.tld --standalone --admin
```

## Limitations

- Wildcard-Zertifikate sind nur mit der Cloudflare DNS API verfügbar.
