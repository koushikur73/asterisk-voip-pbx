# Setup Guide

## 1. Start Ubuntu

```bash
vagrant up
vagrant ssh
```

## 2. Install Asterisk

```bash
sudo apt update
sudo apt install -y asterisk
sudo systemctl enable --now asterisk
```

## 3. Find the server IP

```bash
hostname -I
```

Use the LAN IPv4 address that is reachable from the SIP clients.

## 4. Install configuration

Copy:

```text
asterisk/pjsip.conf
asterisk/extensions.conf
asterisk/rtp.conf
```

to:

```text
/etc/asterisk/
```

For example:

```bash
sudo cp pjsip.conf /etc/asterisk/pjsip.conf
sudo cp extensions.conf /etc/asterisk/extensions.conf
sudo cp rtp.conf /etc/asterisk/rtp.conf
```

Replace both `CHANGE_ME` values in `pjsip.conf`.

## 5. Restart

```bash
sudo systemctl restart asterisk
```

## 6. Verify

```bash
sudo asterisk -rvvv
```

Then:

```text
pjsip show endpoints
pjsip show contacts
```

## 7. Configure SIP clients

Client 1001:

```text
Username: 1001
Password: <configured password>
Server: <Ubuntu LAN IP>
Port: 5060
Transport: UDP
```

Client 1002:

```text
Username: 1002
Password: <configured password>
Server: <Ubuntu LAN IP>
Port: 5060
Transport: UDP
```

## 8. Test

Dial `1002` from `1001`.

Dial `1001` from `1002`.
