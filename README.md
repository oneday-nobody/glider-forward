# glider-forward

機場白嫖設置文件

## 解決咩問題？

1. 好多網站不允許使用 `tor` 訪問，或要做很麻煩嘅 `人機驗證`
2. 唔想直連白嫖機場，理由自己諗

## 要準備啲乜？

1. 有 `tor`, 推薦使用 `docker` run `tor`

```
docker run --rm --name tor-us -p 9050:9050 -v $PWD/torrc-us:/etc/tor/torrc:ro dperson/torproxy
```

> torrc-us

```
ControlSocket /etc/tor/run/control
ControlSocketsGroupWritable 1
ControlPort 9051
CookieAuthentication 1
CookieAuthFileGroupReadable 1
CookieAuthFile /etc/tor/run/control.authcookie
DataDirectory /var/lib/tor
RunAsDaemon 0
User tor
AutomapHostsOnResolve 1
ExitPolicy reject *:*
VirtualAddrNetworkIPv4 10.192.0.0/10
DNSPort 5353
SocksPort 0.0.0.0:9050 IsolateDestAddr
TransPort 0.0.0.0:9040

NewCircuitPeriod 600

StrictNodes 1

ExcludeNodes {cn},{hk},{mo},{sg},{th},{pk},{by},{ru},{ir},{vn},{ph},{my},{cu},{??}
ExcludeExitNodes {cn},{hk},{mo},{sg},{th},{pk},{by},{ru},{ir},{vn},{ph},{my},{cu},{??}

StrictExitNodes 1

ExitNodes 198.98.49.153,198.98.50.112,198.98.50.162,198.98.52.119,198.98.52.169,198.98.52.203,198.98.52.24,198.98.52.75,198.98.54.14,198.98.54.155,198.98.54.170,198.98.54.82,198.98.55.107,198.98.55.233,198.98.55.82,198.98.56.122,198.98.56.27,198.98.56.9,198.98.57.133,198.98.58.149,198.98.58.186,198.98.58.241,198.98.58.27,198.98.58.66,198.98.59.170,198.98.59.197,198.98.59.21,198.98.59.64,198.98.60.123,198.98.60.200,198.98.60.90,198.98.60.92,198.98.62.35,199.195.248.104,199.195.248.43,199.195.249.216,199.195.249.229,199.195.249.57,199.195.249.82,199.195.250.148,199.195.250.42,199.195.250.54,199.195.250.77,199.195.251.110,199.195.251.120,199.195.251.84,199.195.252.144,199.195.252.243,199.195.252.47,199.195.253.74,199.195.254.198

```

2. 有 [glider](https://github.com/nadoo/glider)



## 點用？

1. verify your tor was listen socks5 proxy port at 9050
2. download the `glider-forward.conf`
3. run `glider -listen :8888 -config glider-forward.conf`
4. set your browser use proxy `http://127.0.0.1:8888`
5. done

## 幾時更新?

至少每日更新 4 次
