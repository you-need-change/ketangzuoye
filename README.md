我在github里写了readme（因为当时本地没有markdown编辑器），但是想的是把本地的各种更新同步一下（也就是工程代码在云端更新），但是用git一直提交不了，然后用了很粗暴的办法push -f，虽然上传成功，但是我云端写的readme被覆盖消失了。提交记录里只有之前上传的代码，没有readme。

解决办法：
## 使用github curl工具
要先在github中，`Developer settings`=>`Personal access tokens`，选择`Personal access tokens，Tokens(classic)`或者`Fine-grained tockens`，取决于你需要的权限范围。 
- 如果选择`Tokens(classic)`:
  -点击`Generate new token`。
  -填写令牌描述
  -选择所选的权限范围（例如，`repo`表示对仓库的完全控制）。
  -点击`Generate token`。
- 如果选择`Fine-grained tokens`:
  -点击`Generate new token`。
  -填写令牌描述
  -配置资源访问权限（例如，特定组织或仓库）。
  -配置所需的作用域（例如，读取和写入仓库）。
  -点击`Generate token`。
- 如果您需要取得对仓库的所有权限，则选择`Tokens(classic)`，如果仅需要有限的权限，则选择Fine-grained tokens`。一般只有使用自己系统时，使用的权限更方便。
生成后，你会看到新创建的令牌。非常重要的是，此时需要复制并安全地存储这个令牌，因为一旦离开页面，你就无法再次查看该令牌。（我自己做的时候其实不用令牌也行，浏览器允许就行了。）

![https://github.com/cli/cli?ref_product=cli&ref_type=engagement&ref_style=text#installation](下载github curl工具)

## 使用github curl
- 登录：> gh auth login （一步一步选择就好了，可以用网站就是browser或者token令牌登录）
- 使用![https://developer.github.com/v3/activity/events/]允许浏览最近一次时间：
> curl https://api.github.com/repos/<user>/<repo>/events
"pushEvent"才是应该关注的。

然后可以直接在 GitHub 上创建一个分支（例如last）
