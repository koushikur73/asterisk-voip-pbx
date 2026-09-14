# Troubleshooting

## Registration Failed

Open Asterisk CLI:

```bash
sudo asterisk -rvvv
```

Check:

```text
pjsip show endpoints
pjsip show contacts
```

Enable SIP logging:

```text
pjsip set logger on
```

Try registration again.

If no `REGISTER` appears, investigate network connectivity.

## Check Listening Port

```bash
sudo ss -lunp | grep 5060
```

## Check Firewall

```bash
sudo ufw status
```

If enabled:

```bash
sudo ufw allow 5060/udp
sudo ufw allow 10000:20000/udp
```

## Check VM Network

```bash
hostname -I
ip addr
ip route
```

The SIP clients must be able to reach the Ubuntu VM's LAN address.

## No Audio

Check:

```ini
rtp_symmetric=yes
force_rport=yes
rewrite_contact=yes
direct_media=no
```

Check RTP:

```bash
sudo ss -lunp | grep asterisk
```

## Useful Commands

```text
pjsip show endpoints
pjsip show contacts
pjsip show endpoint 1001
pjsip show endpoint 1002
pjsip show aors
pjsip show auths
pjsip show transports
pjsip set logger on
pjsip set logger off
```
