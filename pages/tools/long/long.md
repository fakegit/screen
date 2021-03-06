---
title: SCP-079-LONG
---

<link rel="stylesheet" href="/css/chinese.css">

**项目编号：**SCP-079-LONG

**项目等级：**Euclid

**特殊收容措施：**SCP-079-LONG 建议在 Linux 环境下运行。Python 3.6 及以上版本可以使用 SCP-079-LONG 。运行所需要安装的第三方模块已在 `requirements.txt` 中列出。务必要注意，其只能通过 SCP-079-USER 邀请入群，并由其赋予管理权限，如果有任何未授权的恶意使用，将可能给其他机器人的工作带来影响。其应该作为频道 SCP-079-CRITICAL 、频道 SCP-079-EXCHANGE 、频道 SCP-079-HIDE 的管理员，并加入 SCP-079-TEST 群组。

**描述：**SCP-079-LONG 是一个用于删除超长消息的机器人，其项目位于 GitLab ，镜像同步并准备（尚未）开源于 <a href="https://github.com/scp-079/scp-079-long" target="_blank">GitHub</a> 。机器人本体位于 <a href="https://t.me/SCP_079_LONG_BOT" class="079" target="_blank">SCP-079-LONG</a> ，仅供经过授权的群组使用，并由群组 SCP-079-MANAGE 中的成员对其进群、退群操作进行管理。其加入了 SCP-079-TEST ，用于测试分析结果。该项目由 ███ 主要负责。通过该项目建立的机器人有类似的功能：根据群组的设置，删除群组中的超长消息，对于在多个群组中以超长消息 spam 的用户进行封禁。具体操作详见附录中的使用说明。

---

**附录：**使用说明

群组中的管理员：

- `/config long`：通过 [SCP-079-CONFIG](/config/) 调整机器人设置，机器人将回报前往设置的链接，5 分钟内设置将被锁定，无法再次更改

除使用 `/config long` 外，管理员也可以通过 `/config_long` 命令在群组中手动调整设置：

- `/config_long show`：显示当前设置
- `/config_long default`：恢复为默认设置
- `/config_long delete off`：关闭协助删除功能
- `/config_long delete on`：开启协助删除功能（默认设置） 
- `/config_long limit 5000`：设置消息字节长度上限，上限应为 1000 的整数倍，并介于 2000 和 10000 之间，默认为 9000

群组中的普通成员：

- `/long`、`/l`：在群组中发送此命令，“强制” 机器人进行超长消息检查，适用于 spam 消息长度超过 10000 字节时使用，此命令会使机器人通过 Bot API 接收到超长消息的 Update

SCP-079-TEST 中的成员：

- `发送超长消息`：显示分析结果
- `/long`、`/l`：强制进行超长消息检查
- `/version`：检查机器人版本

---

**附录：**自建机器人的方法

可先查看<a href="/how-zh/">自建说明书</a>

克隆项目：

```bash
git clone https://gitlab.com/scp-079/scp-079-long.git ~/bots/scp-079/long
```

---

**文件#config.ini：**

修改配置文件：

需要对 `config.ini` 文件中内容为 `[DATA EXPUNGED]` 的全部键值进行修改。 API ID 与 API Hash 在 <a href="https://my.telegram.org" target="_blank">官网</a> 获取

```ini
[proxy]
enabled = False
; 可根据需要自行决定是否使用 SOCKS5 代理
hostname = 127.0.0.1
port = 1080

[basic]
bot_token = [DATA EXPUNGED]
; 此处填写在 @BotFather 处获得的 token
prefix = /!
; 命令前的可用字符，如在群组中使用非常规命令前缀，需要机器人有获取普通消息的权限

[bots]
avatar_id = [DATA EXPUNGED]
; SCP-079-AVATAR 的 ID
captcha_id = [DATA EXPUNGED]
; SCP-079-CAPTCHA 的 ID
clean_id = [DATA EXPUNGED]
; SCP-079-CLEAN 的 ID
lang_id = [DATA EXPUNGED]
; SCP-079-LANG 的 ID
long_id = [DATA EXPUNGED]
; SCP-079-LONG 的 ID
noflood_id = [DATA EXPUNGED]
; SCP-079-NOFLOOD 的 ID
noporn_id = [DATA EXPUNGED]
; SCP-079-NOPORN 的 ID
nospam_id = [DATA EXPUNGED]
; SCP-079-NOSPAM 的 ID
recheck_id = [DATA EXPUNGED]
; SCP-079-RECHECK 的 ID
tip_id = [DATA EXPUNGED]
; SCP-079-TIP 的 ID
user_id = [DATA EXPUNGED]
; SCP-079-USER 的 ID
warn_id = [DATA EXPUNGED]
; SCP-079-WARN 的 ID

[channels]
critical_channel_id = [DATA EXPUNGED]
; 此处填写紧急频道 SCP-079-CRITICAL 的 ID
debug_channel_id = [DATA EXPUNGED]
; 此处填写调试频道 SCP-079-DEBUG 的 ID
exchange_channel_id = [DATA EXPUNGED]
; 此处填写数据交换频道 SCP-079-EXCHANGE 的 ID
; 关于数据交换频道的详情，请查看 https://scp-079.org/exchange/
hide_channel_id = [DATA EXPUNGED]
; 此处填写数据交换备份频道 SCP-079-HIDE 的 ID
logging_channel_id = [DATA EXPUNGED]
; 此处填写证据存放频道 SCP-079-LOGGING 的 ID
test_group_id = [DATA EXPUNGED]
; 此处填写测试群组 SCP-079-TEST 的 ID

[custom]
default_group_link = [DATA EXPUNGED]
; 此处填写调试信息中默认的群组链接
project_link = [DATA EXPUNGED]
; 此处填写项目网址
project_name = [DATA EXPUNGED]
; 此处填写项目名称
punish_time = [DATA EXPUNGED]
; 惩罚用户的时间，期间用户发送的所有带文字的消息将被删除，并且，在此期间内若其发送带文字的消息将重新计时
reset_day = [DATA EXPUNGED]
; 此处填写每月重置数据的日期，例如 1st mon ，代表每月第一个星期一
time_ban = [DATA EXPUNGED]
; 建议追踪封禁状态维持的时间，单位为秒

[encrypt]
key = [DATA EXPUNGED]
; 加密字符串所用的密码
password = [DATA EXPUNGED]
; 加密文件所用的密码
```

---

**附录：**开发备忘

1. 触发超长消息检测者将被删除文本消息，直到用户主动不再发送文本消息一定时间后，该限制自动解除
2. 根据某用户触发超长消息的群组数量，进行 long 评分
3. 如用户评分过高时触发超长消息，或受到追踪删除时触发，将进行追踪封禁类收录，并分享给其他机器人
4. 昵称中含有追踪封禁类词组的用户，如触发超长消息，则进行封禁
5. 将正则表达式计数同步给 REGEX

NOPORN 能够向 ANALYZE、BACKUP、CAPTCHA、CLEAN、CONFIG、LANG、MANAGE、NOFLOOD、NOPORN、NOSPAM、RECHECK、USER、WATCH 发送数据

情形 1：向 BACKUP 传送数据备份文件。每日 UTC 时间 20:00 。`exchange_text` 文本作为该文件的 `caption`

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "BACKUP"
    ],
    action="backup",
    action_type="pickle",
    data="admin_ids"
)
```

情形 2：向 BACKUP 汇报在线状态。每个小时的第 30 分钟

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "BACKUP"
    ],
    action="backup",
    action_type="status",
    data="awake"
)
```

情形 3：向 CONFIG 询问。由于群组管理员在群组中发送 `/config long` 命令，故 LONG 令 CONFIG 在 SCP-079-CONFIG 频道中开启一个更新设置的会话

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "CONFIG"
    ],
    action="config",
    action_type="ask",
    data={
        "project_name": "SCP-079-LONG",
        "project_link": "https://scp-079.org/long/",
        "group_id": -10012345678,
        "group_name": "SCP-079-CHAT",
        "group_link": "https://t.me/SCP_079_CHAT",
        "user_id": 12345678,
        "config": {
            "default": False,
            "lock": 1512345678,
            "limit": 5000
        },
        "default": {
            "default": True,
            "lock": 0,
            "limit": 9000    # 消息的字节长度上限
        }
    }
)
```

情形 4：向 MANAGE 请求。由于没有在管理员列表中找到 SCP-079-USER ，或 USER 管理员身份缺失而请求离开某个群组

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "MANAGE"
    ],
    action="leave",
    action_type="request",
    data={
        "group_id": -10012345678,
        "group_name": "SCP-079-CHAT",
        "group_link": "https://t.me/SCP_079_CHAT",
        "reason": "user"
    }
)
```

情形 5：向 MANAGE 请求。由于管理权限缺失而请求离开某个群组

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "MANAGE"
    ],
    action="leave",
    action_type="request",
    data={
        "group_id": -10012345678,
        "group_name": "SCP-079-CHAT",
        "group_link": "https://t.me/SCP_079_CHAT",
        "reason": "permissions"
    }
)
```

情形 6：向 MANAGE 通知。该机器人已因不在某群组中（确定的非网络原因的 Exception）而自行清空该群组资料

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "MANAGE"
    ],
    action="leave",
    action_type="info",
    data={
        "group_id": -10012345678,
        "group_name": "SCP-079-CHAT",
        "group_link": "https://t.me/SCP_079_CHAT"
    }
)
```

情形 7：向 REGEX 更新规则使用计数文件，每日 UTC 时间 21:00 。`exchange_text` 文本作为该文件的 `caption`

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "REGEX"
    ],
    action="update",
    action_type="download",
    data="wb_words"
)
```

情形 8：向 USER 发送协助请求，调用 delete all 功能，删除某用户全部消息，范围：所有群组（评分过高或受追踪时的触发）

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "USER"
    ],
    action="help",
    action_type="delete",
    data={
        "group_id": -10012345678,
        "user_id": 12345678,
        "type": "global"
    }
)
```

情形 9：向 USER 发送协助请求，调用 global ban 功能，用于查找某用户与机器人的所有共同群组，删除其全部消息，并对其进行限制

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "USER"
    ],
    action="help",
    action_type="ban",
    data={
        "group_id": -10012345678,
        "user_id": 12345678
    }
)
```

情形 10：向其他 Bot（ANALYZE、CAPTCHA、CLEAN、LANG、NOFLOOD、NOPORN、NOSPAM、RECHECK、USER）声明已删除某消息，一定程度上避免对同一条消息重复处理的资源浪费

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "ANALYZE",
        "CAPTCHA",
        "CLEAN",
        "LANG",
        "NOFLOOD",
        "NOPORN",
        "NOSPAM",
        "RECHECK",
        "USER"
    ],
    action="update",
    action_type="declare",
    data={
        "group_id": -10012345678,
        "message_id": 123
    }
)
```

情形 11：向其他 Bot（ANALYZE、CAPTCHA、CLEAN、LANG、MANAGE、NOFLOOD、NOPORN、NOSPAM、RECHECK）更新用户分数

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "ANALYZE",
        "CAPTCHA",
        "CLEAN",
        "LANG",
        "MANAGE",
        "NOFLOOD",
        "NOPORN",
        "NOSPAM",
        "RECHECK"
    ],
    action="update",
    action_type="score",
    data={
        "id": 12345678,
        "score": 0.5
    }
)
```

情形 12：向其他 Bot（ANALYZE、CAPTCHA、CLEAN、LANG、LONG、MANAGE、NOFLOOD、NOPORN、NOSPAM、RECHECK、WATCH）更新用户追踪状态，以 watch ban 为例

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "ANALYZE",
        "CAPTCHA",
        "CLEAN",
        "LANG",
        "MANAGE",
        "NOFLOOD",
        "NOPORN",
        "NOSPAM",
        "RECHECK",
        "WATCH"
    ],
    action="add",
    action_type="watch",
    data={
        "id": 12345678,
        "type": "ban",
        "until"="gAAAAABc1SZjduLGl1872VS6dD3osVJaOSQqdlSHy3SpDXeV4yu2FLbEung8neVMonokt5yI8qaLic8bi44X-y073-pGX6LtxKNQilSvci_gk5xHj4HNPFE="    # 将追踪截止的时间戳转为加密字符串
    }
)
```

情形 13：向其他 Bot（ANALYZE、CAPTCHA、CLEAN、LANG、LONG、MANAGE、NOFLOOD、NOPORN、NOSPAM、RECHECK、USER、WATCH）添加黑名单用户

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "ANALYZE",
        "CAPTCHA",
        "CLEAN",
        "LANG",
        "MANAGE",
        "NOFLOOD",
        "NOPORN",
        "NOSPAM",
        "RECHECK",
        "USER",
        "WATCH"
    ],
    action="add",
    action_type="bad",
    data={
        "id": 12345678,
        "type": "user"
    }
)
```

特殊情形：向所有 bot 发送数据交换频道转移指令

```python
exchange_text = format_data(
    sender="LONG",
    receviers=[
        "EMERGENCY"
    ],
    action="backup",
    action_type="hide",
    data=True
)
```

<audio src="/audio/door/dooropenpage.ogg" autoplay></audio>
<audio id="dooropen079" src="/audio/door/dooropen079.ogg"/>
