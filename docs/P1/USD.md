```mermaid
graph LR
    %% 定义参与者样式
    subgraph Actors [参与者]
        R["👤 需求方 (Requester)"]
        H["👤 服务方 (Helper)"]
        A["🛡️ 管理员 (Admin)"]
    end

    %% 定义系统边界
    subgraph System ["SEI2Hub 校园互助服务平台"]
        direction TB
        UC1((实名身份认证))
        UC2((查询个人信用分))
        
        UC3((发布快递代取))
        UC4((发布学习辅导))
        UC5((发布二手交易))
        UC6((发布组队匹配))
        UC7((支付并冻结资金))
        
        UC8((浏览/检索任务))
        UC9((接受互助任务))
        UC10((上传完成证明))
        UC11((即时通讯沟通))
        
        UC12((确认任务完成))
        UC13((评价对方))
        
        UC14((违规内容审核))
        UC15((争议订单处理))
        UC16((封禁违规账号))
    end

    %% 关联关系
    R --- UC1
    R --- UC2
    R --- UC3
    R --- UC4
    R --- UC5
    R --- UC6
    R --- UC7
    R --- UC11
    R --- UC12
    R --- UC13

    H --- UC1
    H --- UC2
    H --- UC8
    H --- UC9
    H --- UC10
    H --- UC11
    H --- UC13

    A --- UC14
    A --- UC15
    A --- UC16

    %% 包含与扩展关系
    UC3 -.->|include| UC7
    UC4 -.->|include| UC7
    UC12 -.->|extend| UC13