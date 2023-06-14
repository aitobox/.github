## AiToBox 👋

A massive crowdsourced distributed inference cluster Platform for AI Models. It allows people without a powerful GPU to use Stable Diffusion or Large Language Models like Pygmalion/Llama by relying on spare/idle resources provided by the community. It also allows non-python clients, such as games and apps, to use AI-provided generations.

## 说明

AiToBox 旨在建立一个的AI训练众包平台；家里有显卡的小伙伴可以把闲置的设备租出去赚取收益；而没有强力计算设备的用户无需花费大量资金购买设备， 只需登录平台，提交任务即可进行AI训练；

AiToBox -- 让AI训练变得简单

AiToBox是一个创新的AI训练众包平台，为用户提供了无缝连接计算资源和AI训练需求的便捷方式。无论您是有闲置计算设备的用户还是没有强力计算设备的用户，AiToBox都能满足您的需求。

对于有闲置计算设备的用户，AiToBox提供了一个机会来赚取收益。您可以将闲置的显卡设备出租，将其转化为持续的收入来源。通过简单的租赁流程，您可以将您的设备利用起来，无需担心设备闲置浪费。

对于那些想要进行AI训练却无力负担昂贵设备的用户，AiToBox是您的理想选择。无需花费大量资金购买设备，您只需登录平台、提交任务，即可享受到强大的计算资源进行AI训练。而且，我们提供灵活的计费方式，您只需付出极少的费用，即可快速完成您的工作。

AiToBox承诺全面保护用户的隐私。我们采取严格的安全措施，确保您的数据和个人信息得到保护。您可以放心地在平台上进行任务提交和数据处理，享受到安全、可靠的服务。

加入AiToBox，体验智能、高效的AI训练平台，实现您的AI梦想！

# 技术架构

AiToBox 简单的分为 [Client](https://github.com/aitobox/Client) 和[Server](https://github.com/aitobox/Server) 两个部分:


1. Server端功能：
   - 用户注册和认证：提供用户注册和认证功能，确保只有经过验证的用户才能使用平台服务。
   - 任务管理：实现任务创建、分配和执行跟踪功能。将用户提交的任务进行分配给可用的Client端，并跟踪任务的执行状态和进度。
   - 收益统计和分配：记录用户的工作量和收益情况，并根据平台规则进行收益分配。确保公平和透明的收益分配机制。
   - 防作弊机制：实施防作弊机制，采用非对称机密算法确保Client端的安全性和工作量的保护。

2. Client端功能：
   - 安装和配置：用户加入平台后，需要下载和安装Client端程序，并进行必要的配置，包括与Server端的通信设置和密钥管理。
   - 任务接收和执行：Client端接收由Server端分配的任务，执行任务所需的计算操作，并生成结果。
   - 结果上传：完成任务后，Client端使用公钥加密任务结果，然后上传至Server端进行验证和处理。

3. 防作弊机制：
   - 非对称机密算法：为每个Client端生成一对公私钥，Client端只持有公钥。Server端使用私钥对任务进行加密，Client端使用公钥解密任务，以确保任务的安全传输。
   - 结果加密：Client端使用公钥加密任务结果，上传至Server端。Server端使用私钥解密任务结果，确保结果的保密性和完整性。

4. 任务工作量验证和奖励机制：
   - 任务积分：根据任务的计算量大小，为任务分配一定的积分，以反映任务的工作量。
   - 并行执行和结果比对：Server端可以将一个任务分配给多个Client端并行执行，然后将结果进行比对，以确保结果的准确性和一致性。
   - 信用评分：根据Client端的历史记录和表现，进行信用评分，评分高的Client端可以获得更高的任务奖励，激励诚实工作和打击造假。

总体设计目标：保证平台的安全性、可靠性和公平性，促进用户的参与和奖励诚实工作。
