### Build
docker build -t dnsmasq:v0.4.0 .

### RUN 
docker run --name dnsmasq  -d  -p 53:53/udp -p 5380:8080  -v /data/sf-workspaces/docker_file/dnsmasq/dnsmasq.conf:/etc/dnsmasq.conf --restart always dnsmasq:v0.4.0