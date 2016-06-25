# Goldy-client

**goldy-client** is lightweight [DTLS](https://en.wikipedia.org/wiki/Datagram_Transport_Layer_Security)
proxy which allows adding DTLS encryption (using [mbed TLS](https://tls.mbed.org) ) to UDP servers 
without modifying their code.

Note this project is modified based on ibm-security-innovation's  [goldy](https://github.com/ibm-security-innovation/goldy), 
which is targeted for UDP server that does not support DTLS while its client does; similarly this project is targeted
for UDP client that does not support DTLS while the server does (server can support DTLS using goldy).

To build goldy-client from source:

    git clone .../goldy-client.git
    cd goldy-client
    make

Use `make V=1` for a verbose build output and `make DEBUG=1` to enable debug
info (`-g3`).

## Help

    Usage: goldy-client [-hvd] [-g log_level] [-t seconds] -l listen_host:port
                 -b backend_host:port -c cert_pem_file

    Options:
      -h, --help                 this help
      -v, --version              show version and exit
      -d, --daemonize            run as a daemon
      -g, --log=LEVEL            log level DEBUG/INFO/ERROR
      -t, --timeout=SECONDS      Session timeout (seconds)
      -l, --listen=ADDR:PORT     listen for incoming plain UDP packet on addr and UDP port
      -b, --backend=ADDR:PORT    proxy UDP traffic to addr and port with DTLS encrypted
      -c, --cert=FILE            server CA certificate PEM filename

## Deploy guide

By using goldy and goldy-client, user can made a encrypted tunnel which can be used to break GF*W...

You can delopy the service as following...:

### Server side

run goldy and openvpn server(udp mode), openvpn will only accept client proxed from goldy.

### Client side

run goldy-client and openvpn client(udp mode), openvpn will connect to the port goldy-client listens.

## License

Goldy is distributed under the [Apache License, version 2.0](LICENSE) .

(c) Copyright IBM Corp. 2015, 2016

Authors: Dov Murik, Shmulik Regev

Contributions are gladly welcome. Please see the requirement for [Developer Certificate of Origin](CONTRIBUTING.md) .

## Dependencies & 3rd Party

[mbedTLS](https://tls.mbed.org/) is used as the underlying DTLS implementation.

[libev](http://software.schmorp.de/pkg/libev.html) is used as an event library. It's BSD 2 clause license is used.

# Contribution

Contributions to the project are welcomed. It is required however to provide alongside the pull request one of the contribution forms (CLA) that are a part of the project. If the contributor is operating in his individual or personal capacity, then he/she is to use the [individual CLA](./CLA-Individual.txt); if operating in his/her role at a company or entity, then he/she must use the [corporate CLA](CLA-Corporate.txt).

# CAVEATS

Although I can use cacert to verify server certificate now, however I did not enable it due to some reason.

User can modify the code and enable it manually.


