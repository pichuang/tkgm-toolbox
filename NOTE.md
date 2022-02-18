## Ubuntu 20.04 放置自簽憑證 (Certs)
- 主要處理作業系統層級的問題
- 憑證放置位置：/usr/local/share/ca-certificates/
- 檔名務必為 `.crt` 結尾, `.pem` 會認不到
- 不能多張憑證綁在一張 (bundle)，要分開
- 更新 `/etc/ssl/certs`: `update-ca-certificates`
- 測試方式 `openssl s_client -connect harbor.vmware.local:443` Verify return code: 0 (ok)
- 此方式無法解決 `docker login: x509: certificate signed by unknown authority` 問題
- 參考 https://manpages.ubuntu.com/manpages/xenial/man8/update-ca-certificates.8.html

## Docker on Ubuntu 20.04 放置自簽憑證

- `mkdir -p harbor.vmware.local:443`
- `.crt` 跟 `.cert` 結尾對於 docker daemon 定義是不一樣...
```
The Docker daemon interprets .crt files as CA certificates and .cert files as client certificates. If a CA certificate is accidentally given the extension .cert instead of the correct .crt extensiㄍㄍon, the Docker daemon logs the following error message:
```
- 記得要 `systemctl restart docker`

- 參考 https://docs.docker.com/engine/security/certificates/


## Containerd on Ubuntu 20.04 放置自簽憑證


- https://github.com/containerd/containerd/blob/main/docs/cri/registry.md


## Contianer 測試方式

```bash
kubectl run -n default debug-container --restart=Never --rm -i --tty --image harbor.vmware.local/library/debug-container --overrides='{ "apiVersion": "v1", "spec": { "nodeSelector":{"kubernetes.io/hostname":"dev-02180200-md-0-5b77768dcc-29qtk"}}}' -- /bin/bash
```

kubectl run -n default ocp-debug-container --image quay.io/tw_pichuang/debug-container \
  --restart=Never -it --attach --rm \
  --overrides='{ "apiVersion": "v1", "spec": { "nodeSelector":{"kubernetes.io/hostname":"tce-local-control-plane"}, "hostNetwork": true}}' -- /bin/bash
