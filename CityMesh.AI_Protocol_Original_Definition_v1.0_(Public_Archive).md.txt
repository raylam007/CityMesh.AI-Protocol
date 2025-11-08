CityMesh.AI Protocol – Original Definition v1.0
Authored by: Jia Lin (林加), Calgary, Alberta, Canada — November 2025
License: Apache 2.0
Language: English / 中文
Status: Public Technical Description
Version: 1.0
________________________________________
1. Preface / 前言
English:
CityMesh.AI Protocol (CMP/1.0) defines a universal, machine-readable framework that allows AI agents to negotiate, guarantee, and verify local service transactions autonomously.
This document serves as the original description and public declaration of authorship.
中文：
CityMesh.AI 协议（CMP/1.0）定义了一种可被机器读取的通用框架，使 AI 代理能够在本地服务交易中实现自主的议价、托管与验证。
本文为该协议的原始定义与作者公开声明文件。
________________________________________
2. Core Architecture / 协议核心结构
The protocol is defined as a four-phase transaction model:
Phase	Name	Description
1	Request	AI agent A initiates a service request with parameters: ServiceType, TimeWindow, PriceRange, Urgency, TrustScore.
2	Offer	AI agent B responds with dynamic pricing and conditions based on its local data and availability.
3	Escrow	Upon agreement, the system initiates a payment hold (Stripe or similar). Funds remain locked until verification.
4	Proof	After service completion, an encrypted JSON receipt with hash signature (Proof-of-Service) is generated and optionally recorded on a verification network.

该协议采用 四阶段交易模型：
1请求 (Request)： AI 代理 A 发起请求，参数包括服务类型、时间窗口、价格区间、紧急度及信任分数。
2报价 (Offer)： AI 代理 B 根据自身资源和时段生成动态报价与条件。
3托管 (Escrow)： 双方确认后，系统执行资金预授权并托管（如 Stripe 测试模式），在验证完成前冻结资金。
4凭证 (Proof)： 服务完成后，生成带加密签名的 JSON 回执（Proof-of-Service），可选上链验证。
________________________________________

3. Semantic Definition / 语义定义
Minimal Schema (JSON-LD Example):
{
  "@context": "https://schema.citymesh.ai/v1",
  "@type": "ServiceTransaction",
  "Request": {
    "ServiceType": "Cleaning",
    "TimeWindow": "2025-11-10T10:00-12:00",
    "PriceRange": "50-70",
    "Urgency": 0.8,
    "TrustScore": 0.95
  },
  "Offer": {
    "MerchantID": "m123",
    "ProposedPrice": 65,
    "Accepted": true
  },
  "Escrow": {
    "PaymentIntentID": "pi_abc123",
    "Status": "Held"
  },
  "Proof": {
    "CompletionHash": "sha256:xxxxxx",
    "Timestamp": "2025-11-10T12:10:00Z"
  }
}
________________________________________
4. Mechanism Layer / 机制层
•	Broadcast Discovery: Subnet routers broadcast active service agents.
•	Negotiation Logic: Each agent optimizes based on its utility function.
•	Security: All communications signed with keypair; escrow verified by API signature.
•	Failure Recovery: Any failed transaction transitions to DISPUTE with arbitration rules.

•	发现机制： 子网路由广播可用服务节点。
•	议价逻辑： 各代理根据自身效用函数优化报价。
•	安全性： 通讯使用密钥签名，托管经由 API 验证。
•	异常恢复： 失败交易进入 DISPUTE 状态，由仲裁机制处理。
________________________________________



5. License Declaration / 授权声明
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at:
https://www.apache.org/licenses/LICENSE-2.0
You must retain the author attribution:
© 2025 Jia Lin (林加), CityMesh.AI Protocol 1.0

中文摘要：
本协议依据 Apache 2.0 授权发布。任何复制、修改或分发均须保留原作者署名。
若用于衍生系统，须在文档或界面中注明源自 CityMesh.AI 协议 (CMP/1.0)。
________________________________________
6. Timestamp & Hash Proof / 时间戳与哈希验证说明
Procedure Example:
1.	Compute SHA256 hash of this file:
2.	sha256sum CityMesh.AI_Protocol_Original_Definition_v1.0.md
Example output:
sha256: 3f8b9d9a17d0e84e7d2c2c4568abf9c5fba57ef80c7a22a06e445b9a42d9b3ac
3.	Record hash on any public blockchain (Polygon, Arweave, or OpenTimestamps).
4.	Store returned TXID here for permanent verification.
Example Placeholder:
TXID: 0x0000000000000000000000000000000000000000
Date: 2025-11-07

1使用 SHA256 计算文件哈希。
2将哈希上传至任意公共区块链进行存证。
3返回的交易号（TXID）可填入此处，作为时间戳与原创证明。
________________________________________
7. Appendix / 附录
Version History:
•	v1.0 – Initial publication, November 2025
•	Author: Jia Lin (林加)
•	Reviewer: Internal AI Assistant (“Leanne / 黎安”)
Future Extension Tags:
•	CMP/1.1 – Add multi-agent routing and trust index scoring
•	CMP/2.0 – Introduce cross-network negotiation (N2N)
________________________________________
End of Document / 文件结束

