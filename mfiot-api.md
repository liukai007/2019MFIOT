# MFIOT管理端接口文档
+ 2019年4月12日
    + 图片上传接口
    
+ 2019年4月17日
    + 新增用户
    + 删除用户
    + 修改用户
    + 查询用户
    + 管理员修改用户
    + 查询用户列表

    
+ 2019年4月18日
    + 新增设备分类
    + 删除设备分类
    + 修改设备分类
    + 查询设备分类
    + 查询设备分类列表


+ 2019年4月18日
    + 新增主设备
    + 删除主设备
    + 修改主设备
    + 查询主设备
    + 查询主设备列表
    
+ 2019年4月19日
    + 新增楼层
    + 新增会议室
    + 删除位置
    + 修改位置
    + 查询位置
    + 查询位置列表

+ 2019年4月21日
    + 登陆

## 图片上传
### 图片上传接口 [POST] /fileUpload

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
        上传文件即可
        
+ Response 200

        {
            "data": "/iot-img/c3216c00-f0a0-419c-bd6c-2379fd6691b5.jpg"
        }
+ Response 400   

         {
        "data": {
            "msg": "上传格式有问题，请存入后缀是gif,bmp,jpg,jpep,png,tif等常见格式的文件",
            "code": 400
        }
        }

## 用户管理
+ Data
    + username (String) 用户名
    + password (String)  密码
    + headPortrait (String) 头像链接
    + phoneNumber (String) 手机号
    + role (int) 角色（1为管理员 0为普通用户）
    + originalPassword (String) 原密码（修改密码时候使用）
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    
### 新增用户 [POST] /user
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "username": "user001",
            "password":"12345678",
            "headPortrait": "http://www.headPortrait",
            "phoneNumber":"13126822398",
            "role":"1"
        }
        }
+ Response 200

        {
        "data": {
            "id": 30,
            "type": "User"
        }
        }
+ Response 400

        {
        "data": {
            "msg": "手机号码格式不正确",
            "code": 400
        }
        }
        
        {
        "data": {
            "msg": "用户名不允许为空",
            "code": 400
        }
        }
        
        {
        "data": {
            "msg": "默认管理员账号不能占用",
            "code": 400
        }
        }
        
### 删除用户 [DEL] /user/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 200  

        
### 修改用户 [PATCH] /user/{id}

+ Description
    + [MUST] authenticated

+ Request (application/json)
    
        {
        "data": {
            "username": "liukai0099",
            "headPortrait": "http://www.headPortrait",
            "phoneNumber": "13126822398",
            "originalPassword":"budee1234",
            "password":"budee1234"
        }
        }
+ Response 200
+ Response 400

        {
        "data": {
            "msg": "登陆密码不正确，请重新输入",
            "code": 400
        }
        }
        
        {
        "data": {
            "msg": "管理员admin名字不能被修改",
            "code": 400
        }
        }
        
### 管理员修改用户 [PATCH] /user//updateUserByAdmin/{id}  
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "username": "liukai009",
            "phoneNumber": "13126822398",
            "password":"budee1234",
            "role":"0"
        }
        }
+ Response 200
+ Response 400

        {
        "data": {
            "msg": "管理员admin名字不能被修改",
            "code": 400
        }
        }

### 查询用户 [GET] /user/{id}
+ Description
    + [MUST] authenticated
+ Response 200

        {
        "data": {
            "creator": 0,
            "modifier": 1,
            "modified": "2019-04-19 19:11:17",
            "username": "liukai0099",
            "role": 1
        }
        }
### 查询用户分类列表 [GET] /user
+ Description
    + [MUST] authenticated

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[id] (int)    ID  -非必填
    + filter[tel] (String) 电话号  -非必填

+ Response 200

        {
        "meta": {
            "totalPages": 3,
            "totalElements": 21,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": false,
            "sort": null
        },
        "links": {
            "self": "/user?page[number]=1&page[size]=10",
            "first": "/user?page[number]=1&page[size]=10",
            "next": "/user?page[number]=2&page[size]=10",
            "last": "/user?page[number]=3&page[size]=10"
        },
        "data": [
            {
                "creator": 0,
                "modifier": 1,
                "modified": "2019-04-19 19:10:14",
                "username": "admin",
                "role": 1
            },
            {
                "creator": 0,
                "modifier": 1,
                "modified": "2019-04-19 19:11:17",
                "username": "liukai0099",
                "role": 1
            },
            {
                "creator": 0,
                "modifier": 0,
                "username": "admin1",
                "role": 0
            },
            {
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 10:12:49",
                "modified": "2019-04-02 10:12:49",
                "username": "admin22221",
                "role": 0
            },
            {
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 10:18:34",
                "modified": "2019-04-02 10:18:34",
                "username": "admin2222221",
                "role": 0
            },
            {
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 19:12:39",
                "modified": "2019-04-02 19:12:39",
                "username": "LIUKAI007",
                "role": 0
            },
            {
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 20:28:42",
                "modified": "2019-04-02 20:28:42",
                "username": "1233LIUKAI007",
                "role": 0
            },
            {
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-03 10:29:34",
                "modified": "2019-04-03 10:29:34",
                "username": "lk11",
                "role": 0
            },
            {
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-04 11:27:05",
                "modified": "2019-04-04 11:27:05",
                "username": "lk008",
                "role": 1
            },
            {
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-12 14:34:57",
                "modified": "2019-04-12 14:34:57",
                "username": "国产007",
                "role": 0
            }
        ]
        }

## 设备分类管理
+ Data
    + name (String)  设备分类名称
    + description (String) 描述
    + picture (String) 图片链接
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
### 新增设备分类 [POST] /equipmentcategory
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "name": "设备分类",
            "picture":"http://www.picture",
            "description": "describedescribedescribedescribedescribedescribedescribe"
        }
        }
+ Response 200

        {
        "data": {
            "id": 13,
            "type": "EquipmentCategory"
        }
        }
+ Response 400

        {
        "data": {
            "msg": "设备分类名不允许为空",
            "code": 400
        }
        }
        
### 删除设备分类 [DEL] /equipmentcategory/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 200  
+ Response 400

        {
        "data": {
            "msg": "删除设备列表中关联的设备",
            "code": 400
        }
        }
        

### 修改设备分类 [PATCH] /equipmentcategory/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
        {
        "data": {
            "name": "设备分类14",
            "picture":"http://www.picture",
            "description": "describedescribedescribedescribedescribedescribedescribe"
        }
        }

+ Response 200
+ Response 400

        {
        "data": {
            "msg": "设备分类名不允许为空",
            "code": 400
        }
        }

### 查询设备分类 [GET] /equipmentcategory/{id}
+ Description
    + [MUST] authenticated
+ Response 200

        {
        "data": {
            "id": 14,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-04-19 16:19:08",
            "modified": "2019-04-19 16:19:44",
            "name": "设备分类14",
            "description": "describedescribedescribedescribedescribedescribedescribe",
            "picture": "http://www.picture"
        }
        }
### 查询设备分类列表 [GET] /equipmentcategory
+ Description
    + [MUST] authenticated

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[equipmentCategoryId]  设备分类ID  -非必填
    + filter[equipmentCategoryName] (String)  设备分类名称  -非必填（模糊查询）

    
+ Response 200

        {
        "meta": {
            "totalPages": 2,
            "totalElements": 11,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": false,
            "sort": null
        },
        "links": {
            "self": "/equipmentcategory?page[number]=1&page[size]=10",
            "first": "/equipmentcategory?page[number]=1&page[size]=10",
            "next": "/equipmentcategory?page[number]=2&page[size]=10",
            "last": "/equipmentcategory?page[number]=2&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "灯控制器",
                "description": "灯控制器",
                "picture": "http://picturepicturepicturepicture"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "投影机",
                "description": "投影机",
                "picture": "http://picturepicturepicturepicture"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "矩阵切换器",
                "description": "矩阵切换器",
                "picture": "picturepicturepicturepicture"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "中控",
                "description": "中控",
                "picture": "picturepicturepicturepicture"
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "数字音频处理器",
                "description": "数字音频处理器",
                "picture": "picturepicturepicturepicture"
            },
            {
                "id": 6,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "显示器",
                "description": "显示器",
                "picture": "picturepicturepicturepicture"
            },
            {
                "id": 7,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "平板",
                "description": "会议平板",
                "picture": "picturepicturepicturepicture"
            },
            {
                "id": 8,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "name": "投影幕",
                "description": "投影幕",
                "picture": "picturepicturepicturepicture"
            },
            {
                "id": 11,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-18 14:43:21",
                "modified": "2019-04-18 14:45:06",
                "name": "12",
                "description": "测试",
                "picture": "picturepicturepicturepicture"
            },
            {
                "id": 12,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-18 14:48:14",
                "modified": "2019-04-18 17:16:21",
                "name": "222",
                "description": "测试",
                "picture": "picturepicturepicturepicture"
            }
        ]
        }



## 主设备管理
+ Data
    + equipmentCategoryId (Long) 设备分类ID
    + name (String)  设备名字
    + equipPicture (String) 设备图片
    + brand (String)  品牌
    + brandLogo (String) -品牌logo
    + model (String) -型号
    + lifetime (Double)  -寿命（可以说使用最长时间单位小时）
    + description (String) -描述
    + referenceTime (Long) -被会议室引用了次数
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
### 新增主设备 [POST] /equipmentlist

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
        	"equipmentCategoryId":"1",
            "name": "中控001",
            "equipPicture":"http://www.picture",
            "brand":"AMX",
            "brandLogo":"http://www.picture",
            "model": "AMX2001",
            "description": "describedescribedescribedescribedescribedescribedescribe"
        }
        }
+ Response 200

        {
        "data": {
            "id": 10,
            "type": "EquipmentList"
        }
        }
+ Response 400

        {
        "data": {
            "msg": "主设备名称不允许为空",
            "code": 400
        }
        }
+ Response 400
        
        {
        "data": {
            "msg": "已经存在了同品牌，同型号的产品",
            "code": 400
        }
        }

### 删除主设备 [DEL] /equipmentlist/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 200 

+ Response 400

        {
        "data": {
            "msg": "请删掉会议室下面引用的该设备，再来删除该设备",
            "code": 400
        }
        }


### 修改主设备 [PATCH] /equipmentlist/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
        {
        "data": {
        	"equipmentCategoryId":"1",
            "name": "222",
            "equipPicture":"http://www.picture",
            "brand":"AMX1",
            "brandLogo":"http://www.picture",
            "model": "AMX2001",
            "description": "describedescribedescribedescribedescribedescribedescribe"
        }
        }

+ Response 200

### 查询主设备 [GET] /equipmentlist/{id}
+ Description
    + [MUST] authenticated
+ Response 200

        {
        "data": {
        "id": 1,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "equipmentCategoryId": 1,
        "name": "灯控网络接口",
        "brand": "Leviton",
        "brandLogo": "",
        "model": "LNUSB-00B",
        "lifetime": 0
        }
        }
        
### 查询主设备列表 [GET] /equipmentlist
+ Description
    + [MUST] authenticated


+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[id]  (int)   产品ID  -非必填
    + filter[equipmentListId]  主产品ID  -非必填
    + filter[equipmentListName] (String)  主产品名字  -非必填（模糊查询）
    + filter[equipmentCategoryId]  (int) 分类ID -非必填
    
+ Response 200

        {
        "meta": {
            "totalPages": 1,
            "totalElements": 10,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/equipmentlist?page[number]=1&page[size]=10",
            "first": "/equipmentlist?page[number]=1&page[size]=10",
            "last": "/equipmentlist?page[number]=1&page[size]=10"
        },
        "data": [
        {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 1,
            "name": "灯控网络接口",
            "brand": "Leviton",
            "brandLogo": "",
            "model": "LNUSB-00B",
            "lifetime": 0
        },
        {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 6,
            "name": "主席台返看显示器",
            "brand": "SAMSUNG",
            "brandLogo": "",
            "model": "QM65H",
            "lifetime": 0
        },
        {
            "id": 3,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 3,
            "name": "矩阵切换器",
            "brand": "EXTRON",
            "brandLogo": "",
            "model": "XTP II CrossPoint 32",
            "lifetime": 0
        },
        {
            "id": 4,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 2,
            "name": "高清投影机",
            "brand": "BENQ",
            "brandLogo": "",
            "model": "P1660",
            "lifetime": 0
        },
        {
            "id": 5,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 5,
            "name": "数字音频处理器",
            "brand": "EXTRON",
            "brandLogo": "",
            "model": "DMP128",
            "lifetime": 0
        },
        {
            "id": 6,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 2,
            "name": "高清投影机",
            "brand": "NEC",
            "brandLogo": "",
            "model": "PX1005QL",
            "lifetime": 0
        },
        {
            "id": 8,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 7,
            "name": "会议平板",
            "brand": "MAXHUB",
            "brandLogo": "",
            "model": "PC75MJ",
            "lifetime": 0
        },
        {
            "id": 9,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentCategoryId": 8,
            "name": "120寸投影幕（16:10）",
            "brand": "GORSEE",
            "brandLogo": "",
            "model": "GS-E120B",
            "lifetime": 0
        },
        {
            "id": 10,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-04-18 17:29:44",
            "modified": "2019-04-18 17:29:44",
            "equipmentCategoryId": 1,
            "name": "中控001",
            "equipPicture": "http://www.picture",
            "brand": "AMX",
            "brandLogo": "http://www.picture",
            "model": "AMX2001",
            "lifetime": 0
        },
        {
            "id": 13,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-04-18 18:51:08",
            "modified": "2019-04-18 18:52:39",
            "equipmentCategoryId": 1,
            "name": "222",
            "equipPicture": "http://www.picture",
            "brand": "AMX1",
            "brandLogo": "http://www.picture",
            "model": "AMX2001",
            "lifetime": 0,
            "description": "describedescribedescribedescribedescribedescribedescribe"
        }
        ]
        }


## 位置管理
+ Data
    + parentId (long) -父id
    + name (String) -位置名称
    + locationNo (int) -位置码（技术人员填写）
    + description (String) 描述
    + picture (String) 图片链接
    + leaf (int) 是否叶子节点（1为叶子节点 0为非叶子节点）
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
### 新增楼层 [POST] /locations/addfloor

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "name": "11层"
        }
        }
+ Response 200

        {
        "data": {
            "id": 24,
            "type": "Locations"
        }
        }
+ Response 400

        {
        "data": {
            "msg": "已经存在位置名字一样的地点了",
            "code": 400
        }
        }
        
        {
        "data": {
            "msg": "位置名不允许为空",
            "code": 400
            }
        }
+ Response 401 
        
        {
        "data": {
            "msg": "请登陆获取认证",
            "code": 401
        }
        }

### 新增会议室 [POST] /locations/addmeeting

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "parentId": "21",
            "name": "11层大会议室",
            "picture": "http://www.picture",
            "description": "describedescribedescribedescribedescribedescribedescribe",
            "leaf": "1"
        }
        }
+ Response 200

        {
        "data": {
            "id": 26,
            "type": "Locations"
        }
        }
+ Response 400

        {
        "data": {
            "msg": "已经存在位置名字一样的地点了",
            "code": 400
        }
        }
        
        {
        "data": {
            "msg": "位置名不允许为空",
            "code": 400
        }
        }
+ Response 401 
        
        {
        "data": {
            "msg": "请登陆获取认证",
            "code": 401
        }
        }

### 删除位置 [DEL] /locations/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 200  
+ Response 400

        {
        "data": {
            "msg": "请删除该位置下面的所有子位置,再进行删除",
            "code": 400
        }   
        }
        
        
        {
        "data": {
            "msg": "请删除该会议室下面的所有设备,再进行删除",
            "code": 400
        }
        }

### 修改位置 [PATCH] /locations/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
        {
        "data": {
            "name": "11层00",
            "picture": "http://www.picture",
            "description": "describedescribedescribedescribedescribedescribedescribe"
        }
        }

+ Response 200
+ Response 400

        {
        "data": {
            "msg": "已经存在位置名字一样的地点了",
            "code": 400
        }



### 查询位置 [GET] /locations/{id}
+ Description
    + [MUST] authenticated
+ Response 200

        {
        "data": {
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
            "leaf": 1
        }
        }
 
### 通过会议室得到所有设备 [GET] /locations/getSpecificEquipByLocationId/{locationId}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Response 200

        {
        "data": [
            {
            "id": 12,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1012,
            "name": "65寸显示屏",
            "loctionId": 4,
            "equipmentId": 2,
            "meetingRoom": "八层大会议室",
            "categoryName": "显示器"
            },
            {
            "id": 13,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1013,
            "name": "高清投影机",
            "loctionId": 4,
            "equipmentId": 6,
            "meetingRoom": "八层大会议室",
            "categoryName": "投影机"
        },
        {
            "id": 14,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1014,
            "name": "120寸投影幕（16:10）",
            "loctionId": 4,
            "equipmentId": 9,
            "meetingRoom": "八层大会议室",
            "categoryName": "投影幕"
        },
        {
            "id": 15,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1015,
            "name": "数字音频处理器",
            "loctionId": 4,
            "equipmentId": 5,
            "meetingRoom": "八层大会议室",
            "categoryName": "数字音频处理器"
        }
    ]
}


        
### 查询位置列表 [GET] /locations/parentId/{id}
+ Description
    + [MUST] authenticated

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[locationId]  (int)   位置ID  -非必填
    + filter[locationName] (String)  位置名称  -非必填（模糊查询）


+ Response 200

        {
        "meta": {
            "totalPages": 1,
            "totalElements": 6,
            "size": 10,
            "number": 1,
            "numberOfElements": 6,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/locations/parentId/1?page[number]=1&page[size]=10",
            "first": "/locations/parentId/1?page[number]=1&page[size]=10",
            "last": "/locations/parentId/1?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-15 15:54:32",
                "modified": "2019-04-15 16:02:36",
                "parentId": 1,
                "name": "楼一层",
                "locationNo": 0,
                "description": "楼一层",
                "leaf": 0
            },
            {
                "id": 17,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "parentId": 1,
                "name": "楼五层",
                "locationNo": 0,
                "leaf": 0
            },
            {
                "id": 18,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "parentId": 1,
                "name": "楼六层",
                "locationNo": 0,
                "leaf": 0
            },
            {
                "id": 19,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "parentId": 1,
                "name": "楼七层",
                "locationNo": 0,
                "leaf": 0
            },
            {
                "id": 20,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "parentId": 1,
                "name": "楼八层",
                "locationNo": 0,
                "leaf": 0
            },
            {
                "id": 21,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "modified": "2019-04-19 14:19:41",
                "parentId": 1,
                "name": "11层00",
                "locationNo": 0,
                "description": "describedescribedescribedescribedescribedescribedescribe",
                "picture": "http://www.picture",
                "leaf": 0
            }
            ]
            }
        
   
## 登陆
### 登陆接口
+ Description
+ Request (application/json)
    
        {
        "data": {
            "username": "liukai",
            "password": "budee123"
        }
        } 

+ Response 200
     //得到了cookie   

        {
        "data": {
            "Cookie": "JSESSIONID=9080F1D07B0C45B8F1C5564DB861B5AF"
        }
        }
    
+ Response 400

       {
        "data": {
            "msg": "用户名或密码输入错误",
            "code": 400
        }
        } 
