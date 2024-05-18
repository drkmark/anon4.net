# dns4.cc
crew operates free independent "network" of 9 DNSCrypt servers spread around the gloge to keep your browsing safe and secure. 

all our servers are **public, dnssec capable, non-blocking, non-logging and non-filtered** and work like DNSCrypt public resolvers and/or anonymization relays. 


to start using our network simply add the lists of dns4.cc servers and anonymization relays into your `dnscrypt-proxy.toml` config, restart the service and enjoy. 

> right, we bravely expect you've installed dnscrypt-proxy on your endpoint already. :wink:
> if not, visit [dnscrypt-proxy repo](https://github.com/DNSCrypt/dnscrypt-proxy) for more details and return here when done. theory and other useful info would be found at [DNSCrypt website](https://dnscrypt.info/).


1. either download dns4.cc repository as ZIP or clone dns4.cc repository to anywhere like 
    ```
    git https://git clone https://github.com/drkmark/dns4.cc.git
    ```
and copy all the files to dnscrypt-proxy working directory (i.e. /opt/dnscrypt-proxy/)
    

2. in `[sources]` section of your `dnscrypt-proxy.toml` configuration file you should add something like:

    a. dns4.cc public resolvers

    ```
    [sources.'dns4.cc-resolvers.md']
        urls = ['https://raw.githubusercontent.com/drkmark/dns4.cc/main/dns4.cc-resolvers.md']
        cache_file = 'dns4.cc-resolvers.md'DNSCrypt
        minisign_key = 'OURPUBLICMINISIGNKEYGOESHERE'
        refresh_delay = 72
    ```

    b. dns4.cc anonymization relays

```
    [sources.'dns4.cc-relays.md']
        urls = ['https://raw.githubusercontent.com/drkmark/dns4.cc/main/dns4.cc-relays.md']
        cache_file = 'dns4.cc-relays.md'DNSCrypt
        minisign_key = 'OURPUBLICMINISIGNKEYGOESHERE'
        refresh_delay = 72
```

3. in `[anonymized_dns]` section then add routes as needed, i.e. (or as you wish):

```    
    routes = [
        { server_name='dns4.cc-us-ca-ipv4', via=['anon-dns4.cc-us-ny-ipv4'], via=['anon-dns4.cc-us-tx-ipv4'] },
        { server_name='dns4.cc-vn-ipv6', via=['anon-dns4.cc-hk-ipv6'], via=['anon-dns4.cz-ipv6'] },
        .....
        ]
```
btw. it isn't needed to be "superanonymized" via more than 1-2 relays as latency would inceases dramaticaly.
just check and play with routes to test latency i.e. with [DNS leak script](https://github.com/macvk/dnsleaktest/blob/master/dnsleaktest.sh) from [@macvk](https://github.com/macvk).


read "/your/dncrypt-proxy/working-directory/"`example-dnscrypt-proxy.toml` for proper settings!


- [list of dns4.cc public resolvers](https://raw.githubusercontent.com/drkmark/dns4.cc/main/dns4.cc-resolvers.md)
- [list of dns4.cc anonymization relays](https://raw.githubusercontent.com/drkmark/dns4.cc/main/dns4.cc-relays.md)

********************

DNS servers locations as of May 2024:

### US
 - San Jose, CA
 - Dallas, TX
 - Buffalo, NY

### Europe
 - Coventry, UK
 - Frankfurt Am Main, Germany
 - Budweis, Czechia
 - Bratislava, Slovakia

### Asia/Pacific
 - Ho Chi Minh City, Vietnam
 - Hong Kong, China


********************

...and that's all, folks. have a good time!

©2024 darkmark & dns4.cc crew
