# MFIOT北京银行界面接口文档
+ 2019年4月21日
    + 中控设备占比图接口

+ 2019年7月2日
    + 受控设备分类统计图
    + 受控设备分类统计表
    + 会议室统计接口
    + 设备统计接口
    + 中控设备统计接口

+ 2019年7月3日
    + 列出品牌接口
    + 列出设备分类接口
    + 列出楼层接口
    + 通过楼层得到会议室接口
    + 设备状态接口
    

+ 2019年7月8日
    + 会议室列表
    + 会议室详情接口

+ 2019年7月9日
    + 会议室最近一年使用情况接口
    + 中控主机与受控设备状态接口
    + 上月会议室使用排行接口
    + 会议室使用情况趋势图接口
    

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
            
### 列出品牌接口 [GET]  /brand/info
+ Data
    + id (int) ID
    + brandName (String) 品牌名称
    + brandLogo (String) 品牌logo

+ Description
+ Response 200  

        {
        "data": [
            {
                "id": 1,
                "brandName": "Leviton",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 2,
                "brandName": "SAMSUNG",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 3,
                "brandName": "EXTRON",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 4,
                "brandName": "BENQ",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 5,
                "brandName": "NEC",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 6,
                "brandName": "MAXHUB",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 7,
                "brandName": "GORSEE",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 8,
                "brandName": "AMX",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 9,
                "brandName": "AMX1",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            }
        ]
        }
            
### 列出设备分类接口 [GET]  /equipmentcategory/info

+ Data
    + id (int) id
    + name (String) 分类名字
    + description (Int) 描述
    + picture (String) 分类的图片

+ Description
+ Response 200  

        {
        "data": [
            {
                "id": 1,
                "name": "灯控制器",
                "description": "灯控制器",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            },
            {
                "id": 2,
                "name": "投影机",
                "description": "投影机",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            },
            {
                "id": 3,
                "name": "矩阵切换器",
                "description": "矩阵切换器",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            },
            {
                "id": 4,
                "name": "中控",
                "description": "中控",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            },
            {
                "id": 5,
                "name": "数字音频处理器",
                "description": "数字音频处理器",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            },
            {
                "id": 6,
                "name": "显示器",
                "description": "显示器",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            },
            {
                "id": 7,
                "name": "平板",
                "description": "会议平板",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            },
            {
                "id": 8,
                "name": "投影幕",
                "description": "投影幕",
                "picture": "https://static.mifanxing.com/wx/image/95/20/1335046.jpg"
            }
        ]
        }

### 列出楼层接口 [GET]  /locations/floor

+ Data
    + id (int) ID
    + name (String) 楼层名字
    + description (String) 楼层描述
    + picture  (String) 楼层图片

+ Description
+ Response 200  

        {
        "data": [
            {
                "id": 17,
                "name": "楼五层",
                "description": "1"
            },
            {
                "id": 18,
                "name": "楼六层",
                "description": "1"
            },
            {
                "id": 19,
                "name": "楼七层",
                "description": "2"
            },
            {
                "id": 20,
                "name": "楼八层",
                "description": "2"
            },
            {
                "id": 21,
                "name": "11层00",
                "description": "describedescribedescribedescribedescribedescribedescribe",
                "picture": "http://www.picture"
            }
        ]
        }

### 通过楼层得到会议室接口 [GET] /locations/meetingroombyfloor/{floor_id}     

+ Data
    + id (int)
    + name (String) 会议室名称
    + description  (String)  描述
    + picture (String) 图片

+ Description
+ Parameters
    + floor_id (int)  楼层ID  -必填 
+ Response 200  

        {
        "data": [
            {
                "id": 5,
                "name": "六层会议室",
                "description": "六层会议室",
                "picture": "http://www.bankofbeijing.com.cn/images/logo.gif"
            }
        ]
        }

### 设备状态接口 [GET] /specificequip

/specificequip?filter[brandIds]=1,2&filter[equipmentCategoryIds]=1,2,3,6&page[number]=1&page[size]=5&filter[locationId]=x

+ Data
    + id (int) ID
    + enabled (int)  1使能  0禁用
    + creator (int) 创建人ID
    + modifier (int) 修改人ID
    + modified  (datetime) 修改时间
    + equipmentNo (int) 自定义编码
    + name (String) 设备名字
    + locationId (int) 位置ID
    + equipmentId (int)  设备ID
    + usedTime (int)  已经使用时长
    + presentStatueId (int) 设备状态 0关闭，1正常 ，2故障
    + picture  (String) 设备图片
    + useNumber (int) 使用次数
    + failureNumber (int) 故障次数
    + whetherMonitor (int) 是否被监控1监控 0非监控
    + meetingRoom  (String)  会议室名字
    + categoryName  (String) 分类名字
    + floorId (int) 楼层ID
    + floorName (String) 楼层名字
    + model  (String)  型号
    + brandName  (String)  品牌名字
    
+ Description
+ Parameters
    + page[number] (int)  页码 -非必填 默认为1
    + page[size] (int)  页尺 -非必填 默认为10
    + filter[locationId] (int) 位置id (可以是楼层ID,也可以说会议室id,如果是楼层id，就把该楼层所有会议室都查出来，如果是会议室id，只查该会议室)
    + filter[brandIds] (String) 非必填 品牌id,使用逗号隔开
    + filter[equipmentCategoryIds] (String) 非必填 分类id，使用逗号隔开
+ Response 200  

        {
        "meta": {
            "totalPages": 1,
            "totalElements": 4,
            "size": 5,
            "number": 1,
            "numberOfElements": 4,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/specificequip?filter[brandIds]=1,2&filter[equipmentCategoryIds]=1,2,3,6&page[number]=1&page[size]=5",
            "first": "/specificequip?filter[brandIds]=1,2&filter[equipmentCategoryIds]=1,2,3,6&page[number]=1&page[size]=5",
            "last": "/specificequip?filter[brandIds]=1,2&filter[equipmentCategoryIds]=1,2,3,6&page[number]=1&page[size]=5"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "modified": "2019-04-16 13:31:37",
                "equipmentNo": 1001,
                "name": "灯控网络接口",
                "locationId": 3,
                "equipmentId": 1,
                "usedTime": 5,
                "presentStatueId": 1,
                "picture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "useNumber": 1,
                "failureNumber": 1,
                "whetherMonitor": 0,
                "meetingRoom": "一层大报告厅",
                "categoryName": "灯控制器",
                "floorName": "11层00",
                "floorId": 21,
                "model": "LNUSB-00B",
                "brandName": "Leviton"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "modified": "2019-04-16 13:34:00",
                "equipmentNo": 1002,
                "name": "主席台返看显示器",
                "locationId": 3,
                "equipmentId": 2,
                "usedTime": 4,
                "presentStatueId": 1,
                "picture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "useNumber": 2,
                "failureNumber": 1,
                "whetherMonitor": 0,
                "meetingRoom": "一层大报告厅",
                "categoryName": "显示器",
                "floorName": "11层00",
                "floorId": 21,
                "model": "QM65H",
                "brandName": "SAMSUNG"
            },
            {
                "id": 12,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "equipmentNo": 1012,
                "name": "65寸显示屏",
                "locationId": 4,
                "equipmentId": 2,
                "usedTime": 3,
                "presentStatueId": 1,
                "picture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "useNumber": 12,
                "failureNumber": 1,
                "whetherMonitor": 0,
                "meetingRoom": "八层大会议室",
                "categoryName": "显示器",
                "floorName": "楼八层",
                "floorId": 20,
                "model": "QM65H",
                "brandName": "SAMSUNG"
            },
            {
                "id": 16,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "equipmentNo": 1016,
                "name": "65寸显示屏",
                "locationId": 8,
                "equipmentId": 2,
                "usedTime": 8,
                "presentStatueId": 1,
                "picture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "useNumber": 16,
                "failureNumber": 1,
                "whetherMonitor": 0,
                "meetingRoom": "八层会议室",
                "categoryName": "显示器",
                "floorName": "楼八层",
                "floorId": 20,
                "model": "QM65H",
                "brandName": "SAMSUNG"
            }
        ]
        }
         
### 会议室列表 [GET] /locations/meetingRoom

+ Data
    + id (int) ID
    + enabled (int)  1使能  0禁用
    + creator (int) 创建人ID
    + modifier (int) 修改人ID
    + modified  (datetime) 修改时间
    + parentId  (int) 父id
    + name (string)  位置名字
    + locationNo (int)  自定义id
    + description (string) 描述
    + picture (string) 图片链接
    + systemDiagram (string) 系统图链接
    + leaf (int) 是否叶子节点 1为叶子节点 0为非叶子节点
    + floor (int) 是否楼层 1为楼层 0为非楼层
    + status (int) 状态 0未使用状态 1为使用 2为故障
    
+ Description
+ Parameters
    + page[number] (int)  页码 -非必填 默认为1
    + page[size] (int)  页尺 -非必填 默认为10
+ Response 200  

        {
        "meta": {
            "totalPages": 1,
            "totalElements": 7,
            "size": 10,
            "number": 1,
            "numberOfElements": 7,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/locations/meetingRoom?page[number]=1&page[size]=10",
            "first": "/locations/meetingRoom?page[number]=1&page[size]=10",
            "last": "/locations/meetingRoom?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "modified": "2019-04-15 16:02:25",
                "parentId": 21,
                "name": "一层大报告厅",
                "locationNo": 1001,
                "description": "一层会议室",
                "picture": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "leaf": 1,
                "floor": 0,
                "status": 0
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "modified": "2019-04-15 16:02:11",
                "parentId": 20,
                "name": "八层大会议室",
                "locationNo": 1005,
                "description": "八层大会议室",
                "picture": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "leaf": 1,
                "floor": 0,
                "status": 0
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "modified": "2019-04-15 16:05:53",
                "parentId": 18,
                "name": "六层会议室",
                "locationNo": 1003,
                "description": "六层会议室",
                "picture": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "leaf": 1,
                "floor": 0,
                "status": 0
            },
            {
                "id": 6,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "parentId": 17,
                "name": "五层会议室",
                "locationNo": 1002,
                "description": "五层会议室",
                "picture": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "leaf": 1,
                "floor": 0,
                "status": 0
            },
            {
                "id": 7,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "parentId": 19,
                "name": "七层会议室",
                "locationNo": 1004,
                "description": "七层会议室",
                "picture": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "leaf": 1,
                "floor": 0,
                "status": 0
            },
            {
                "id": 8,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "parentId": 20,
                "name": "八层会议室",
                "locationNo": 1006,
                "description": "八层会议室",
                "picture": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "leaf": 1,
                "floor": 0,
                "status": 0
            },
            {
                "id": 26,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-19 13:49:03",
                "modified": "2019-04-19 14:03:13",
                "parentId": 21,
                "name": "11层大会议室",
                "locationNo": 0,
                "description": "describedescribedescribedescribedescribedescribedescribe",
                "picture": "http://www.picture",
                "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
                "leaf": 1,
                "floor": 0,
                "status": 0
            }
        ]
    }
 
### 会议室详情接口 [GET]  /locations/{id}

+ Data
    + id (int) ID
    + enabled (int)  1使能  0禁用
    + creator (int) 创建人ID
    + modifier (int) 修改人ID
    + modified  (datetime) 修改时间
    + parentId  (int) 父id
    + name (string)  位置名字
    + locationNo (int)  自定义id
    + description (string) 描述
    + picture (string) 图片链接
    + systemDiagram (string) 系统图链接
    + leaf (int) 是否叶子节点 1为叶子节点 0为非叶子节点
    + floor (int) 是否楼层 1为楼层 0为非楼层
    + status (int) 状态 0未使用状态 1为使用 2为故障
    + weekUseNumber  (int) 周使用次数

+ Description
+ Parameters
    + id (int) 位置ID  -必填 
+ Response 200  

        {
        "data": {
            "id": 3,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "modified": "2019-04-15 16:02:25",
            "parentId": 21,
            "name": "一层大报告厅",
            "locationNo": 1001,
            "description": "一层会议室",
            "picture": "http://www.bankofbeijing.com.cn/images/logo.gif",
            "systemDiagram": "http://www.bankofbeijing.com.cn/images/logo.gif",
            "leaf": 1,
            "floor": 0,
            "status": 0,
            "weekUseNumber": 1
        }
        }
        
### 会议室最近一年使用情况接口 [GET] /locations/recentYear/{location_id}

+ Data
    + Map<String,int> 年-月：次数

+ Description
+ Parameters
    + location_id (int)  会议室ID  -必填 
+ Response 200  

        {
        "data": {
            "2019-06": 3,
            "2019-05": 3,
            "2019-07": 4,
            "2019-02": 0,
            "2018-11": 0,
            "2019-01": 0,
            "2018-12": 0,
            "2019-04": 0,
            "2019-03": 0,
            "2018-10": 0,
            "2018-08": 0,
            "2018-09": 0
        }
        }
        
### 中控主机与受控设备状态接口 [GET] /specificequip
例如：http://127.0.0.1:8999/specificequip?filter[isCenterControl]=1&filter[locationId]=8

+ Data
    + id (int) ID
    + enabled (int)  1使能  0禁用
    + creator (int) 创建人ID
    + modifier (int) 修改人ID
    + modified  (datetime) 修改时间
    + equipmentNo (int) 自定义编码
    + name (String) 设备名字
    + locationId (int) 位置ID
    + equipmentId (int)  设备ID
    + usedTime (int)  已经使用时长
    + presentStatueId (int) 设备状态 0关闭，1正常 ，2故障
    + picture  (String) 设备图片
    + useNumber (int) 使用次数
    + failureNumber (int) 故障次数
    + whetherMonitor (int) 是否被监控1监控 0非监控
    + meetingRoom  (String)  会议室名字
    + categoryName  (String) 分类名字
    + floorId (int) 楼层ID
    + floorName (String) 楼层名字
    + model  (String)  型号
    + brandName  (String)  品牌名字  
    + brandLogo  (String) 品牌logo
    + averWeekRunNumber (float) 周平均运行次数
    + weekRunNumber (Map<周几，次数>) 周每日运行次数

+ Description
+ Parameters
    + filter[locationId] (int)  会议室ID  -必填
    + filter[isCenterControl]  (int)  是否是中控 1为中控 0为非中控
+ Response 200  

        {
        "meta": {
            "totalPages": 1,
            "totalElements": 1,
            "size": 10,
            "number": 1,
            "numberOfElements": 1,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/specificequip?filter[isCenterControl]=1&filter[locationId]=8&page[number]=1&page[size]=10",
            "first": "/specificequip?filter[isCenterControl]=1&filter[locationId]=8&page[number]=1&page[size]=10",
            "last": "/specificequip?filter[isCenterControl]=1&filter[locationId]=8&page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 20,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "equipmentNo": 0,
                "name": "中控ev",
                "locationId": 8,
                "equipmentId": 10,
                "usedTime": 1,
                "presentStatueId": 1,
                "picture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "useNumber": 20,
                "failureNumber": 1,
                "whetherMonitor": 0,
                "meetingRoom": "八层会议室",
                "categoryName": "中控",
                "floorName": "楼八层",
                "floorId": 20,
                "model": "AMX2001",
                "brandName": "AMX",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "weekRunNumber": {
                    "1": 1,
                    "2": 0,
                    "3": 1,
                    "4": 2,
                    "5": 3,
                    "6": 3,
                    "7": 0
                },
                "averWeekRunNumber": 1.2
            }
        ]
    }
        
### 上月会议室使用排行接口 [GET]  /logs/usetimerank

+ Data
    + id (int) ID
    + name (string) 会议室名字
    + locationNo (int) 月使用次数

+ Description
+ Parameters
+ Response 200  

        {
        "data": [
            {
                "id": 26,
                "name": "11层大会议室",
                "locationNo": 122
            },
            {
                "id": 7,
                "name": "七层会议室",
                "locationNo": 111
            },
            {
                "id": 5,
                "name": "六层会议室",
                "locationNo": 10
            },
            {
                "id": 38,
                "name": "11层会议室11",
                "locationNo": 8
            },
            {
                "id": 37,
                "name": "11层会议室10",
                "locationNo": 1
            },
            {
                "id": 39,
                "name": "11层会议室12",
                "locationNo": 1
            },
            {
                "id": 3,
                "name": "一层大报告厅",
                "locationNo": 0
            },
            {
                "id": 4,
                "name": "八层大会议室",
                "locationNo": 0
            },
            {
                "id": 6,
                "name": "五层会议室",
                "locationNo": 0
            },
            {
                "id": 8,
                "name": "八层会议室",
                "locationNo": 0
            },
            {
                "id": 27,
                "name": "11层会议室1",
                "locationNo": 0
            },
            {
                "id": 28,
                "name": "11层会议室2",
                "locationNo": 0
            },
            {
                "id": 29,
                "name": "11层会议室3",
                "locationNo": 0
            },
            {
                "id": 31,
                "name": "11层会议室4",
                "locationNo": 0
            },
            {
                "id": 32,
                "name": "11层会议室5",
                "locationNo": 0
            },
            {
                "id": 33,
                "name": "11层会议室6",
                "locationNo": 0
            },
            {
                "id": 34,
                "name": "11层会议室7",
                "locationNo": 0
            },
            {
                "id": 35,
                "name": "11层会议室8",
                "locationNo": 0
            },
            {
                "id": 36,
                "name": "11层会议室9",
                "locationNo": 0
            }
        ]
        }

### 会议室使用情况趋势图接口 [GET] /logs/usedcondition

+ Data
    + id (int) ID
    + name (string) 会议室名字
    + locationNo (int) 使用次数

+ Description
+ Parameters
    + filter[year] (string)  年 -必填
    + filter[month] (string) 月
    + filter[day] (string) 日
+ Response 200   

        {
        "data": [
            {
                "id": 3,
                "name": "一层大报告厅",
                "locationNo": 0
            },
            {
                "id": 4,
                "name": "八层大会议室",
                "locationNo": 0
            },
            {
                "id": 5,
                "name": "六层会议室",
                "locationNo": 0
            },
            {
                "id": 6,
                "name": "五层会议室",
                "locationNo": 0
            },
            {
                "id": 7,
                "name": "七层会议室",
                "locationNo": 0
            },
            {
                "id": 8,
                "name": "八层会议室",
                "locationNo": 0
            },
            {
                "id": 26,
                "name": "11层大会议室",
                "locationNo": 0
            },
            {
                "id": 27,
                "name": "11层会议室1",
                "locationNo": 0
            },
            {
                "id": 28,
                "name": "11层会议室2",
                "locationNo": 0
            },
            {
                "id": 29,
                "name": "11层会议室3",
                "locationNo": 0
            },
            {
                "id": 31,
                "name": "11层会议室4",
                "locationNo": 0
            },
            {
                "id": 32,
                "name": "11层会议室5",
                "locationNo": 0
            },
            {
                "id": 33,
                "name": "11层会议室6",
                "locationNo": 0
            },
            {
                "id": 34,
                "name": "11层会议室7",
                "locationNo": 0
            },
            {
                "id": 35,
                "name": "11层会议室8",
                "locationNo": 0
            },
            {
                "id": 36,
                "name": "11层会议室9",
                "locationNo": 0
            },
            {
                "id": 37,
                "name": "11层会议室10",
                "locationNo": 0
            },
            {
                "id": 38,
                "name": "11层会议室11",
                "locationNo": 0
            },
            {
                "id": 39,
                "name": "11层会议室12",
                "locationNo": 1
            }
        ]
    }
