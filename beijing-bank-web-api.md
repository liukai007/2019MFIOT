# MFIOT北京银行界面接口文档
+ 2019年4月21日
    + 中控设备占比图接口

+ 2019年7月2日
    + 受控设备分类统计图
    + 受控设备分类统计表
    + 会议室统计接口
    + 设备统计接口
    + 中控设备统计接口
    

### 中控设备占比图接口 [GET] /equipmentlist/equip_category/4
+ Data
    + totalCount (int) 中控设备总数量
    + id (int)  ID
    + enabled (int) 使能 1启用 0禁用
    + creator  (int) 创建人id
    + modifier (int) 修改人id
    + created (date) 创建日期
    + modified (date) 修改日期
    + equipmentCategoryId (int) 分类id
    + name (String) 设备名称
    + equipPicture  (String) 设备图片
    + brand  (String) 品牌名字
    + brandLogo  (String) 品牌logo
    + model  (String) 型号
    + lifetime  (float) 使用寿命
    + description  (String) 描述
    + whetherControlled (int) 是否受控1受控 0不受控
    + referenceTime (int)  被引用了几次
+ Description
+ Response 200

        {
        "data": {
            "totalCount": 2,
            "map": {
                "中控001": {
                    "id": 10,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-04-18 17:29:44",
                    "modified": "2019-04-18 17:29:44",
                    "equipmentCategoryId": 4,
                    "name": "中控001",
                    "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                    "brand": "AMX",
                    "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                    "model": "AMX2001",
                    "lifetime": 0,
                    "description": "desc",
                    "whetherControlled": 0,
                    "referenceTime": 1
                },
                "中控002": {
                    "id": 13,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-04-18 18:51:08",
                    "modified": "2019-04-18 18:52:39",
                    "equipmentCategoryId": 4,
                    "name": "中控002",
                    "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                    "brand": "AMX1",
                    "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                    "model": "AMX2001",
                    "lifetime": 0,
                    "description": "describedescribedescribedescribedescribedescribedescribe",
                    "whetherControlled": 0,
                    "referenceTime": 1
                }
            }
        }
        }

### 受控设备分类统计图 [GET] /equipmentlist/controlled_equipment/cartogram/
+ Data
    + totalEquipmentCount (int) 受控设备数量
    + categoryCountMap (Map<String,long>)  分类名字和设备数量

+ Description
    + [MUST] authenticated
    
+ Response 200  

        {
        "data": {
            "totalEquipmentCount": 19,
            "categoryCountMap": {
                "投影机": 3,
                "显示器": 3,
                "投影幕": 3,
                "数字音频处理器": 5,
                "灯控制器": 1,
                "平板": 3,
                "矩阵切换器": 1
            }
        }
        }
            
###  受控设备分类统计表 [GET]  
/equipmentlist?filter[whetherControlled]=1
+ Data
    + id (int)  ID
    + enabled (int) 使能 1启用 0禁用
    + creator  (int) 创建人id
    + modifier (int) 修改人id
    + created (date) 创建日期
    + modified (date) 修改日期
    + equipmentCategoryId (int) 分类id
    + name (String) 设备名称
    + equipPicture  (String) 设备图片
    + brand  (String) 品牌名字
    + brandLogo  (String) 品牌logo
    + model  (String) 型号
    + lifetime  (float) 使用寿命
    + description  (String) 描述
    + whetherControlled (int) 是否受控1受控 0不受控
    + referenceTime (int)  被引用了几次

+ Description
+ Parameters
    + page[number] (int)  页码  -非必填 默认为1
    + page[size]   页尺 -非必填 默认10

+ Response 200  

        {
        "meta": {
            "totalPages": 2,
            "totalElements": 8,
            "size": 5,
            "number": 1,
            "numberOfElements": 5,
            "first": true,
            "last": false,
            "sort": null
        },
        "links": {
            "self": "/equipmentlist?filter[whetherControlled]=1&page[number]=1&page[size]=5",
            "first": "/equipmentlist?filter[whetherControlled]=1&page[number]=1&page[size]=5",
            "next": "/equipmentlist?filter[whetherControlled]=1&page[number]=2&page[size]=5",
            "last": "/equipmentlist?filter[whetherControlled]=1&page[number]=2&page[size]=5"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-02 15:52:33",
                "modified": "2019-07-02 15:52:36",
                "equipmentCategoryId": 1,
                "name": "灯控网络接口",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brand": "Leviton",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "LNUSB-00B",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-02 15:52:30",
                "modified": "2019-07-02 15:52:39",
                "equipmentCategoryId": 6,
                "name": "主席台返看显示器",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brand": "SAMSUNG",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "QM65H",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-02 15:52:26",
                "modified": "2019-07-02 15:52:42",
                "equipmentCategoryId": 3,
                "name": "矩阵切换器",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brand": "EXTRON",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "XTP II CrossPoint 32",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-02 15:52:23",
                "modified": "2019-07-02 15:52:44",
                "equipmentCategoryId": 2,
                "name": "高清投影机",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brand": "BENQ",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "P1660",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-02 15:52:19",
                "modified": "2019-07-02 15:52:47",
                "equipmentCategoryId": 5,
                "name": "数字音频处理器",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brand": "EXTRON",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "DMP128",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            }
            ]
            }
            
### 会议室统计接口 [GET] /locations/usedstatus
+ Data
    + weekUsageRate (float) 周使用率
    + linkRelativeRatio (float) 环比
    + inkRelativeRatioUpDown (Int) 1为上升，0为下降
    + weekUsageHighest (String) 上周使用率最高的会议室
    + totalCount (Long)  会议室总间数

+ Description
+ Response 200  

        {
        "data": {
            "weekUsageRate": 13,
            "linkRelativeRatio": 12,
            "linkRelativeRatioUpDown": 1,
            "weekUsageHighest": "六层会议室",
            "totalCount": 7
        }
        }

### 设备统计接口 [GET] /specificequip/usedstatus
+ Data
    + weekUsageRate (float) 周使用率
    + linkRelativeRatio (float) 环比
    + inkRelativeRatioUpDown (Int) 1为上升，0为下降
    + weekUsageHighest (String) 上周使用率最高的设备
    + totalCount (Long)  设备总数

+ Description
+ Response 200  

        {
        "data": {
            "weekUsageRate": 14.4,
            "linkRelativeRatio": 11,
            "linkRelativeRatioUpDown": 1,
            "weekUsageHighest": "投影机",
            "totalCount": 21
        }
        }
        
### 中控设备统计接口 [GET] /specificequip/usedstatus/centercontrol
+ Data
    + weekUsageRate (float) 周使用率
    + linkRelativeRatio (float) 环比
    + inkRelativeRatioUpDown (Int) 1为上升，0为下降
    + weekUsageHighest (String) 上周使用率最高的中控设备
    + totalCount (Long)  会议室总间数

+ Description
+ Response 200  

        {
        "data": {
            "weekUsageRate": 14.8,
            "linkRelativeRatio": 11,
            "linkRelativeRatioUpDown": 1,
            "weekUsageHighest": null,
            "totalCount": 2
        }
        }
            
            
            
            
            
            
            
            
