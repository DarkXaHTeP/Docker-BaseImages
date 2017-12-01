FROM arm32v6/alpine:3.6

WORKDIR /consul

RUN apk add --no-cache ca-certificates curl \
    && curl https://releases.hashicorp.com/consul/1.0.1/consul_1.0.1_linux_arm.zip -o consul.zip \
    && unzip consul.zip \
    && rm consul.zip \
    && apk del ca-certificates curl

RUN mkdir -p /consul/data && \
    mkdir -p /consul/config

# Server RPC is used for communication between Consul clients and servers for internal
# request forwarding.
EXPOSE 8300

# Serf LAN and WAN (WAN is used only by Consul servers) are used for gossip between
# Consul agents. LAN is within the datacenter and WAN is between just the Consul
# servers in all datacenters.
EXPOSE 8301 8301/udp 8302 8302/udp

# HTTP and DNS (both TCP and UDP) are the primary interfaces that applications
# use to interact with Consul.
EXPOSE 8500 8600 8600/udp

ENTRYPOINT ["./consul"]

CMD ["agent", "-dev", "-client", "0.0.0.0"]
