# QR-V™ SDK

Developer SDKs for QR-V™ should target the consolidated two-node architecture.

## Human-facing URLs

```text
https://qrv.network/verify/{QRVID}
https://qrv.network/registry/{QRVID}
https://qrv.network/docs
https://qrv.network/developers
```

## Machine-facing API

```text
https://api.qrv.network/api/v1
```

SDKs should use `api.qrv.network` for programmatic verification, issuance, revocation, and authorized registry operations. They should generate human verification links using `qrv.network/verify/{QRVID}`.

Legacy service subdomains are compatibility aliases and should not be introduced into new SDK defaults.
