```bash
PS C:\Users\90986\Desktop> npm i hexo-cli -g

added 53 packages in 19s
npm notice
npm notice New minor version of npm available! 10.7.0 -> 10.8.1
npm notice Changelog: https://github.com/npm/cli/releases/tag/v10.8.1
npm notice To update run: npm install -g npm@10.8.1
npm notice
PS C:\Users\90986\Desktop> npm install -g npm@10.8.1

removed 2 packages, and changed 63 packages in 11s
PS C:\Users\90986\Desktop> hexo -v
hexo : 无法加载文件 D:\Program Files\nodejs\hexo.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.micros
oft.com/fwlink/?LinkID=135170 中的 about_Execution_Policies。
所在位置 行:1 字符: 1
+ hexo -v
+ ~~~~
    + CategoryInfo          : SecurityError: (:) []，PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
PS C:\Users\90986\Desktop> sudo npm i hexo-cli -g
sudo : 无法将“sudo”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保路径正确
，然后再试一次。
所在位置 行:1 字符: 1
+ sudo npm i hexo-cli -g
+ ~~~~
    + CategoryInfo          : ObjectNotFound: (sudo:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\90986\Desktop> npm i hexo-cli -g
npm : 无法加载文件 D:\Program Files\nodejs\npm.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsof
t.com/fwlink/?LinkID=135170 中的 about_Execution_Policies。
所在位置 行:1 字符: 1
+ npm i hexo-cli -g
+ ~~~
    + CategoryInfo          : SecurityError: (:) []，PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
PS C:\Users\90986\Desktop> get-ExecutionPolicy
Restricted
PS C:\Users\90986\Desktop> Set-ExecutionPolicy -Scope CurrentUser

位于命令管道位置 1 的 cmdlet Set-ExecutionPolicy
请为以下参数提供值:
ExecutionPolicy: 1
PS C:\Users\90986\Desktop> RemoteSigned
RemoteSigned : 无法将“RemoteSigned”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径
，请确保路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ RemoteSigned
+ ~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (RemoteSigned:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\90986\Desktop> get-ExecutionPolicy
RemoteSigned
PS C:\Users\90986\Desktop> npm install -g npm@10.8.1

changed 13 packages in 3s
PS C:\Users\90986\Desktop> hexo -v
hexo-cli: 4.3.2
os: win32 10.0.22631 undefined
node: 20.15.0
acorn: 8.11.3
ada: 2.7.8
ares: 1.28.1
base64: 0.5.2
brotli: 1.1.0
cjs_module_lexer: 1.2.2
cldr: 45.0
icu: 75.1
llhttp: 8.1.2
modules: 115
napi: 9
nghttp2: 1.61.0
nghttp3: 0.7.0
ngtcp2: 1.1.0
openssl: 3.0.13+quic
simdutf: 5.2.8
tz: 2024a
undici: 6.13.0
unicode: 15.1
uv: 1.46.0
uvwasi: 0.0.21
v8: 11.3.244.8-node.23
zlib: 1.3.0.1-motley-7d77fb7
PS C:\Users\90986\Desktop>
```
