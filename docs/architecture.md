# Architecture

```text
                  Local Network
                       |
       +---------------+---------------+
       |                               |
   SIP Client                       SIP Client
      1001                             1002
       |                               |
       +---------------+---------------+
                       |
                +------v------+
                |   Asterisk  |
                |   PJSIP PBX |
                +------+------+
                       |
                Ubuntu VM
             Vagrant + VirtualBox
```

### Components

- Asterisk: SIP server/IP-PBX
- PJSIP: SIP endpoints, authentication and contacts
- SIP: signaling
- RTP: voice media
- Vagrant/VirtualBox: Ubuntu virtualization
