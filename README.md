# CSense

> 一个 CCW 安全审计工具。

火速冲冲冲！[https://axolotltfgs.github.io/CSense/csense.js](点击下载 CSense，一分钱都不要!)

## 功能

- 一键登录新身份，甚至都不需要密码！（官方更新后功能略有瑕疵）
- 一键下载 CCW 的闭源作品，监视、修改、锁定克隆体变量，轻松搞定。
- 一键改数据库，CCWData 内容随你改，作品和用户数据库都能动。
- 快速解锁成就，随心所欲修改附加说明和排行榜名次。
- 一键运行合约规则，提取币池内资产/注入币池。
- 编写脚本（CSense Scripting API），自动化寻找变量，懒人福音。

以下功能还在开发中：

- 管理 MMO 房间（锁定/监视房间信息/追踪玩家列表/伪踢出/调整多登/发送命令），按正则无视远程 MMO 数据。

## 目的

联机枪战、长风银行、鸭里奥、cave.io、小猫派对... CCW 的无数作品在滥用扩展构建空中楼阁。安全性和反作弊？没人在意那种东西。

Scratch 原版在安全性和服务器资源/易读性的二选一中选择了后者，添加了云变量。

几乎所有 Scratch 的二次开发都沿用了这个设计，Gandi IDE 更是“登峰造极”，试图把整个多人联机系统、数据库和社区机制建立在这个有问题的机制上。

举个例子，MMO 现在的身份认证方式就是发送一些公开数据，攻击者可以轻松伪造“公开数据”，假装成别人。

如果换成发送 token，攻击者又能截取 token 来盗号。最终的解决方案是构建一套服务器认证系统，虽然工作量大，但能完美解决伪造问题。

然而，问题远不止身份伪造。攻击者可以伪造封禁名单（代理 ccwdata），实现被封仍能登录，甚至无视某个玩家的消息/管理命令，轻松伪踢出/提权。

如果官方听到用户的错误呼吁，给 MMO 加了踢出积木，攻击者也能利用这个积木迅速踢出所有人，整个 MMO 将变成黑客大战。

根本原因是 Scratch 没有后端，所有本该在后端处理的操作都放到了客户端，结果这些操作都能被劫持。

以前觉得用 Scratch 写后端是痴人说梦，但 CCW 作为一个融资数亿的公司，想实现这个功能其实不难。

可惜 CCW 选择无视这一点，在有问题的设计上继续添砖加瓦，最终导致“步子太大扯到蛋”，一切都无法挽回。

同时，CCW 社区太过高估了盗源的难度。然而，只要是个 Scratch 二次开发就能被盗源。

虽然有如 ClipCC 等平台在 `toJSON` 上动了手脚，导致盗源作品无法正常加载，但只要将社区版的导出逻辑应用到 vm 上，盗源依然能行。

CCW 社区不仅在盗源上认识错误，部分“知识分子”（包括官方）对 vm 这个概念过于敏感，仿佛 vm 就是盗源的源头，因此 CCW 从未开放过 vm。

可惜，vm 并不是盗源的开始，作品序列化只需 runtime 的内容就足够了。如果想禁止盗源，应该关闭对 runtime 的访问权限。

即使将 vm 保护得再严密，也能通过一套通用逻辑从 React 框架提取出实例。这也是 CSense 获取 vm 的原理。

因此，我们制作并匿名发布这个工具的目的是：
1. 将 CCW 变成一个仅限实名认证账户的平台，或让它的安全措施变得最严格。
2. 让 CCW 和扩展开发者们醒醒，告诉他们在本地处理数据是不安全的这个常识。
3. 推动 Scratch 后端开发的产生。
4. 让开发者可以测试自己应用程序的安全性。

## 开发人员名单

- Axolotl / 匿名1 / 匿名2 - 开发
- Tin_Dunwi - 美术、开发协力
- OpenAI GPT-4 - 文本

部分开发者不愿透露身份，特此以“匿名”表示。

## 用户协议

CSense 属于 Public Domain，只要你有本事，随便你怎么改、怎么发、怎么二次创作！不过为了防止滥用，我们加了一点混淆和完整性保护的小手段。

请不要用 CSense 去干那些违法或者可能惹麻烦的事，我们不会为你的行为买单。如果你滥用这个工具，法律不会放过你的。希望你能好好利用这个工具，让 CCW 变得更好！
