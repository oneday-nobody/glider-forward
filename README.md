# glider-forward

機場白嫖設置文件

## 解決咩問題？

1. 好多網站不允許使用 `tor` 訪問，或要做很麻煩嘅 `人機驗證`
2. 唔想直連白嫖機場，理由自己諗

## 點用？

1. verify your tor was listen socks5 proxy port at 9050
2. download the `glider-forward.conf`
3. run `glider -listen :8888 -config glider-forward.conf`
4. set your browser use proxy `http://127.0.0.1:8888`
5. done

## 幾時更新?

至少每日更新 4 次
