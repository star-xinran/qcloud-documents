认证策略包含 PeerAuthentication 和 RequestAuthentication。其中，PeerAuthentication 策略用于配置服务通信的 mTLS 模式，RequestAuthentication 策略用于配置服务的请求身份验证方法。

## PeerAuthentication 配置字段说明

以下是 PeerAuthentication 重要字段说明：

| 字段名称 | 字段类型 | 字段说明 |
| ----- | ---- | ----- |
| `metadata.name` | `string` | PeerAuthentication 名称 | 
| `metadata. namespace` | `string` | PeerAuthentication 命名空间 | 
| `spec.selector` | `map<string, string>` | PeerAuthentication 使用填写的标签键值对，配合填写的namespace，匹配配置下发的 Workload 范围，namespace 填写 istio-system，且 selector 字段不填写时，该策略生效范围为整个网格；namespace 填写非 istio-system 的 namespace，且 selector 字段不填写时，策略生效范围为填写的 namespace；namespace 填写非 istio-system 的 namespace，且 selector 字段填写了有效键值对时，策略的生效范围为在所填 namespace 下根据 selector 匹配到的Workload |
| `spec.mtls.mode` | - | 配置 mTLS 的模式，支持：`UNSET|DISABLE|PERMISSIVE|STRICT` 四种模式，UNSET 模式为继承父范围的 mTLS 模式（如有），否则视为 PERMISSIVE 模式；DISABLE 模式为明文连接，不使用 mTLS 加密（不推荐使用），同时需要配置相同应用范围的 DestinationRule TLS 模式为 DISABLE 使用；PERMISSIVE 模式连接可以是明文或密文，业务改造过程中推荐使用此模式；STRICT 模式下连接必须使用 mTLS 加密。 |
| `spec.portLevelMtls` | `map<uint32, mTLS mode>` | 设置端口级别的 mTLS 模式 |

mTLS 模式配置，不同选择范围的生效效力为：端口 > 服务/Workload > namespace > 网格。

## 使用 PeerAuthentication 配置网格内服务通信 mTLS 模式

### YAML 配置示例

### 控制台配置示例

## RequestAuthentication 配置字段说明

## 使用 RequestAuthentication 配置请求 JWT 认证

### YAML 配置示例

### 控制台配置示例