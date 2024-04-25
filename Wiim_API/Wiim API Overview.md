# Wiim Audio Device API Documentation

## Overview

This document describes the HTTP API for controlling Wiim audio devices. The API allows for interaction with Wiim devices for various functionalities such as playback control, retrieving device status, and more.

## Base URL

Replace `{your-wiim-device-ip}` with the actual IP address of your WiiM device.

https://{your-wiim-device-ip}/

## Security

All requests must be sent over HTTPS and require TLS 1.2 for secure communication.

## Abstract

> Assuming a device IP address of `192.168.10.1`, the general request format would look like:

```html
 GET http://192.168.10.1/httpapi.asp?command={command}
```

To communicate with a board you have to send `HTTP GET` requests.  
The response is in `JSON` format.

<aside class="notice">
All response examples in this documentation are from different devices (<strong>Up2Stream Amp v4</strong>, <strong>Up2Stream mini v3</strong>) but same firmware version (<code>4.6.327252.26</code>). It is possible that responses from older firmware may differ.
</aside>

## Header

For all requests, the following keys are mandatory:

| Key           | Value             |
|---------------|-------------------|
| `Accept`      | `application/json`|
| `Content-Type`| `application/json`|