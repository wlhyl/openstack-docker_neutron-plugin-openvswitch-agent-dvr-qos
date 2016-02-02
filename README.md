# 环境变量
- RABBIT_HOST: rabbitmq IP
- RABBIT_USERID: rabbitmq user
- RABBIT_PASSWORD: rabbitmq user 的 password
- KEYSTONE_INTERNAL_ENDPOINT: keystone internal endpoint
- KEYSTONE_ADMIN_ENDPOINT: keystone admin endpoint
- NEUTRON_PASS: openstack neutron密码
- LOCAL_IP: tunel ip

# volumes:
- /etc/neutron/: /etc/neutron

# 启动neutron-plugin-openvswitch-agent
```bash
docker run -d --name neutron-plugin-openvswitch-agent \
    -v /etc/neutron/:/etc/neutron \
    -e RABBIT_HOST=10.64.0.52 \
    -e RABBIT_USERID=openstack \
    -e RABBIT_PASSWORD=openstack \
    -e KEYSTONE_INTERNAL_ENDPOINT=10.64.0.52 \
    -e KEYSTONE_ADMIN_ENDPOINT=10.64.0.52 \
    -e NEUTRON_PASS=neutron_pass \
    -e LOCAL_IP=172.168.0.10 \
    10.64.0.50:5000/lzh/neutron-plugin-openvswitch-agent:kilo
```