# QuantumultX-myself

个人 Quantumult X 规则与脚本合集。

## PCDN 拦截规则

- 文件：[Womsxd-PCDN-QuantumultX.list](Womsxd-PCDN-QuantumultX.list)
- 上游：[Womsxd/MyAdBlockRules](https://github.com/Womsxd/MyAdBlockRules/blob/master/p2pcdnblock.txt)
- 转换程序：`convert.py`
- 自动检查：配置为每 5 分钟一次；GitHub Actions 实际调度可能延迟。内容变化才提交，也可手动运行。
- QX 订阅：https://raw.githubusercontent.com/jeb-oshe/QuantumultX-myself/main/Womsxd-PCDN-QuantumultX.list

### 转换覆盖与限制

2026-11-05 核对：上游有 61 条有效规则（60 条去重），包括 57 条域名规则和 4 条正则。57 条域名规则及 3 条快手正则已映射为 70 条去重后的 QX 分流规则。

按用户选择，下列斗鱼正则保留未转换，避免扩大拦截范围：

```text
/trk-([0-9\-]+)\.douyucdn\.cn/
```

QX 的域名通配符不能精确表示这里的数字/连字符字符集与无限重复；`trk-*.douyucdn.cn` 会扩大匹配范围，因此没有采用。此订阅不是上游规则的 100% 等价副本。其余映射针对域名匹配用途，不能宣称与 Adblock 的完整 URL 匹配语义完全等价。

出现新的不支持语法时，转换程序报错并保留已发布文件，避免静默丢失规则。规则文件中的 PCDN 和 Womsxd 是功能及来源名称，文件名保留以兼容已有订阅。

## IP 地理位置查询

- 文件：[IP_API.js/IP_API.js](IP_API.js/IP_API.js)
- 上游：[KOP-XIAO/QuantumultX](https://github.com/KOP-XIAO/QuantumultX/blob/master/Scripts/IP_API.js)
- 同步时自动在副标题加入出口 IP；上游预期代码变化时停止同步并报错。
- 自动检查：配置为每 5 分钟一次，内容变化才提交，也可手动运行。
- 查询服务：ip-api.com。

```ini
geo_location_checker=http://ip-api.com/json/?lang=zh-CN,https://raw.githubusercontent.com/jeb-oshe/QuantumultX-myself/main/IP_API.js/IP_API.js
```

## QX 格式参考

[Quantumult X 官方 sample.conf](https://github.com/crossutility/Quantumult-X/blob/master/sample.conf)
