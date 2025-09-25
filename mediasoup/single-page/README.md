
# Mediasoup POC

A minimal mediasoup demo app for cross-browser video calls with the simplest possible signaling and dependencies.

### What it demonstrates:

- Send/receive audio & video
- Switch input devices and replace tracks
- Screen sharing
- Subscribe/unsubscribe to tracks
- Independently pause for sender/receiver
- Simulcast set max layer when sending/receiving
- Stats display and “active speaker” indicator

### How to run locally:

```bash
npm install 
DEBUG="mediasoup*, demo-app*" npm run start → open http://localhost:3000/.
```
Try a second tab or window for multi-party. Use checkboxes to pause and radio buttons to change simulcast layers.

Clients on other machines:
Enable HTTPS by setting sslCrt/sslKey in config.js (self-signed is fine). Add external IPs in webRtcTransport.listIps. If HTTPS keys are present, the server starts as HTTPS—confirm via console.

### AWS EC2

- Allow inbound TCP :3000, inbound UDP :40000–49999, all outbound.
- On Amazon Linux install g++ (e.g., gcc72-c++) and Node via nvm then clone npm install.
- Set listenIps with the instances private IP and announcedIp with its public IPv4.


### Notes
- No WebSockets just a few HTTP endpoints.
- All server code in server.js, client code in client.js.