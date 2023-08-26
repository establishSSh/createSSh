# 第一步:建立ssh
```
ssh-keygen
```
## 然後到~/.ssh/id_rsa.pub 打開並且將其放到github 帳號設定中
### ~/.ssh 在windows 使用者中
複雜化指令如下
```
ssh-keygen \
    -m PEM \ 方式 預設:PEM
    -t rsa \編碼模式
    -b 4096 \ 預設:4096
    -C "azureuser@myserver" \ 註解
    -f ~/.ssh/id_rsa \ ~/簡短版路徑若不行，請使用fullPath
    -N mypassphrase 通關密碼 github個人帳號不要設置
```

## 建立完 ssh 以後 ~/.ssh 將被建立 ，建立一個config 檔案
config 檔案內容如下:
# Github Personal
```
Host personal
    user XXX
    HostName github.com
    IdentityFile ~/.ssh/id_rsa
```
等同於 ssh XXX@github.com
# GitHub Company
```
Host company
    user XXX
    HostName github.com
    IdentityFile ~/.ssh/id_rsa_company
```


# 建立完以後先確認是否與github連線
```
start-ssh-agent
```
就會把電腦的公鑰加進去
```
ssh -T git@github.com 與github連線
```
### 就能進行下一步，驗證fingerPrint是否正確 如果正確 就可以按yes

## 重要:(https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints)
ECDSA key fingerprint is ``this is a gribbish dont care``
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,XX.XX.XXX.XXX' (``ECDSA``) to the list of known hosts.
```
this is a gribbish dont care
```
確定上述的fingerprint 是跟github對得起來的
# 配置如下(#以此篇為例)
ssh 會變成:git@personal:establishSSh/createSSh.git

### 完成教學
