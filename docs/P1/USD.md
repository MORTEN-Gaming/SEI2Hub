```mermaid
useCaseDiagram
    actor "Requester (发布者)" as R
    actor "Helper (接单者)" as H
    actor "Admin (平台管理员)" as A

    package "SEI2Hub 校园互助服务平台" {
        usecase "实名身份认证" as UC1
        usecase "查询个人信用分" as UC2
        
        usecase "发布快递代取任务" as UC3
        usecase "发布学习辅导任务" as UC4
        usecase "发布二手交易商品" as UC5
        usecase "发布组队匹配信息" as UC6
        usecase "支付并冻结资金 (ESC)" as UC7
        
        usecase "浏览/检索任务" as UC8
        usecase "接受互助任务" as UC9
        usecase "上传任务完成证明" as UC10
        usecase "即时通讯沟通" as UC11
        
        usecase "确认任务完成" as UC12
        usecase "评价对方" as UC13
        
        usecase "违规内容审核" as UC14
        usecase "争议订单处理" as UC15
        usecase "封禁违规账号" as UC16
    }

    %% 通用用例
    R --> UC1
    R --> UC2
    H --> UC1
    H --> UC2
    
    %% 发布者相关
    R --> UC3
    R --> UC4
    R --> UC5
    R --> UC6
    R --> UC7
    R --> UC11
    R --> UC12
    R --> UC13

    %% 接单者相关
    H --> UC8
    H --> UC9
    H --> UC10
    H --> UC11
    H --> UC13

    %% 管理员相关
    A --> UC14
    A --> UC15
    A --> UC16
    
    %% 包含关系示例
    UC3 ..> UC7 : <<include>>
    UC4 ..> UC7 : <<include>>
    UC12 ..> UC13 : <<extend>>