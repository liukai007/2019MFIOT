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
    + 登出

+ 2019年4月22日
    + 新增指定设备
    + 删除指定设备
    + 修改指定设备
    + 查询指定设备
    + 查询会议室ID查询指定设备列表

+ 2019年8月1日
    + 新增品牌
    + 删除品牌
    + 修改品牌
    + 查询品牌
    + 查询品牌列表
    + 通过名字查询品牌

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
          "username": "user001111",
          "password":"12345678",
          "headPortrait": "http://www.headPortrait",
          "phoneNumber":"13126822398",
          "email":"df@df.com",
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
            "username": "admin",
            "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
            "phoneNumber": "13326822398",
            "email": "850@qq.com",
            "role": 1,
            "password":"budee1234",
            "originalPassword":"budee123"
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
        
### 管理员修改用户 [PATCH] /user/updateUserByAdmin/{id}  
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
            "modified": "2019-04-19 19:10:14",
            "username": "admin",
            "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
            "phoneNumber": "13126822398",
            "email": "850@qq.com",
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
                "id": 1,
                "creator": 0,
                "modifier": 1,
                "modified": "2019-04-19 19:10:14",
                "username": "admin",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 1
            },
            {
                "id": 2,
                "creator": 0,
                "modifier": 1,
                "modified": "2019-04-19 19:11:17",
                "username": "liukai",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 1
            },
            {
                "id": 3,
                "creator": 0,
                "modifier": 0,
                "username": "admin1",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 0
            },
            {
                "id": 5,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 10:12:49",
                "modified": "2019-04-02 10:12:49",
                "username": "admin22221",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 0
            },
            {
                "id": 6,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 10:18:34",
                "modified": "2019-04-02 10:18:34",
                "username": "admin2222221",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 0
            },
            {
                "id": 8,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 19:12:39",
                "modified": "2019-04-02 19:12:39",
                "username": "LIUKAI007",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 0
            },
            {
                "id": 9,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-02 20:28:42",
                "modified": "2019-04-02 20:28:42",
                "username": "1233LIUKAI007",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 0
            },
            {
                "id": 10,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-03 10:29:34",
                "modified": "2019-04-03 10:29:34",
                "username": "lk11",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 0
            },
            {
                "id": 12,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-04 11:27:05",
                "modified": "2019-04-04 11:27:05",
                "username": "lk008",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
                "role": 1
            },
            {
                "id": 14,
                "creator": 1,
                "modifier": 1,
                "created": "2019-04-12 14:39:39",
                "modified": "2019-04-12 14:39:39",
                "username": "国产0071",
                "headPortrait": "https://static.mifanxing.com/iyyren/image/201609/16/1725/120297960490811392.jpg",
                "phoneNumber": "13126822398",
                "email": "850@qq.com",
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
    + id (int) ID
    + equipmentCategoryId (Long) 设备分类ID
    + name (String)  设备名字
    + equipPicture (String) 设备图片
    + brandId  (int) 品牌id
    + brand (String)  品牌
    + brandLogo (String) -品牌logo
    + model (String) -型号
    + lifetime (Double)  -寿命（可以说使用最长时间单位小时）
    + description (String) -描述
    + whetherControlled (String) 1为受控 0为不受控
    + referenceTime (Long) -被会议室引用了次数
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
}

    
### 新增主设备 [POST] /equipmentlist

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "equipmentCategoryId": "1",
            "name": "中控001",
            "equipPicture": "http://www.picture",
            "brandId": "1",
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
            "equipmentCategoryId": "1",
            "name": "中控001",
            "equipPicture": "http://www.picture",
            "brandId": "1",
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
            "created": "2019-07-02 15:52:33",
            "modified": "2019-07-02 15:52:36",
            "equipmentCategoryId": 1,
            "name": "灯控网络接口",
            "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
            "brandId": 1,
            "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
            "model": "LNUSB-00B",
            "lifetime": 0,
            "description": "desc",
            "whetherControlled": 1,
            "referenceTime": 0
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
                "created": "2019-07-03 03:52:33",
                "modified": "2019-07-03 03:52:36",
                "equipmentCategoryId": 1,
                "name": "灯控网络接口",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 1,
                "brand": "Leviton1",
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
                "created": "2019-07-03 03:52:30",
                "modified": "2019-07-03 03:52:39",
                "equipmentCategoryId": 6,
                "name": "主席台返看显示器",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 2,
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
                "created": "2019-07-03 03:52:26",
                "modified": "2019-07-03 03:52:42",
                "equipmentCategoryId": 3,
                "name": "矩阵切换器",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 3,
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
                "created": "2019-07-03 03:52:23",
                "modified": "2019-07-03 03:52:44",
                "equipmentCategoryId": 2,
                "name": "高清投影机",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 4,
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
                "created": "2019-07-03 03:52:19",
                "modified": "2019-07-03 03:52:47",
                "equipmentCategoryId": 5,
                "name": "数字音频处理器",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 3,
                "brand": "EXTRON",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "DMP128",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 6,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 03:52:17",
                "modified": "2019-07-03 03:52:50",
                "equipmentCategoryId": 2,
                "name": "高清投影机",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 5,
                "brand": "NEC",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "PX1005QL",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 8,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 03:52:15",
                "modified": "2019-07-03 03:52:53",
                "equipmentCategoryId": 7,
                "name": "会议平板",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 6,
                "brand": "MAXHUB",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "PC75MJ",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 9,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 03:52:12",
                "modified": "2019-07-03 03:52:56",
                "equipmentCategoryId": 8,
                "name": "120寸投影幕（16:10）",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 7,
                "brand": "GORSEE",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "GS-E120B",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 1,
                "referenceTime": 0
            },
            {
                "id": 10,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-19 05:29:44",
                "modified": "2019-04-19 05:29:44",
                "equipmentCategoryId": 4,
                "name": "中控001",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 8,
                "brand": "AMX",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "AMX2001",
                "lifetime": 0,
                "description": "desc",
                "whetherControlled": 0,
                "referenceTime": 0
            },
            {
                "id": 13,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-19 06:51:08",
                "modified": "2019-04-19 06:52:39",
                "equipmentCategoryId": 4,
                "name": "中控002",
                "equipPicture": "https://static.mifanxing.com/yyren/image/149/53/3511737.jpg?w=200",
                "brandId": 9,
                "brand": "AMX1",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90",
                "model": "AMX2001",
                "lifetime": 0,
                "description": "describedescribedescribedescribedescribedescribedescribe",
                "whetherControlled": 0,
                "referenceTime": 0
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


        
### 查询位置列表 [GET] /locations/parentId  （通过parend_id得到所有的位置）
+ Description
    + [MUST] authenticated

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[locationId]  (int)   位置ID  -非必填 默认值是1（1为起始位置id）
    + filter[locationName] (String)  位置名称  -非必填（模糊查询）
    + filter[floor] (int) 是否floor 0所有位置   1楼层


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

### 登陆接口 [POST] /login

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

### 登出接口 [GET] /logout

+ Description
+ Response 200

        {
        "data": {
            "logout": "logout success"
        }
        }
        

## 指定设备管理（实际会议室使用设备）
+ Data
    + equipmentNo (int) -设备编号号（记录日志使用）
    + name (String)  -设备名称
    + loctionId (long) -位置的id(主要是设备的id)
    + equipmentId (long) -主设备的id
    + ip (String) -IP地址 （比如中控需要使用ip地址）
    + port (long) -端口 （比如中控需要使用ip地址）
    + uniqueIdentification -唯一识别码（可以说sn）
    + usedTime (long) -已经使用时长
    + presentStatueId (long) -当前状态ID
    + picture (String) -图片链接
    + meetingRoom (String) -会议室名字
    + categoryName (String) -设备分类的名字
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
### 新增指定设备 [POST] /specificequip
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "equipmentNo": 10012,
            "loctionId":12,
            "equipmentId":222,
            "ip":"192.168.1.1",
            "port":8080,
            "uniqueIdentification":"fff",
            "usedTime":"1000",
            "presentStatueId":"1",
            "picture":"http://wwww"
        }
        }
+ Response 200

        {
        "data": {
            "id": 23,
            "type": "SpecificEquip"
        }
        }
+ Response 400

        {
        "data": {
            "msg": "主设备ID不允许为空",
            "code": 400
        }
        }
        
        {
        "data": {
            "msg": "位置ID不允许为空",
            "code": 400
        }
        }
        
### 删除指定设备 [DEL] /specificequip/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 200  


### 修改指定设备 [PATCH] /specificequip/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
        {
        "data": {
            "equipmentNo": 10012,
            "loctionId":12,
            "ip":"192.168.1.1",
            "port":8080,
            "uniqueIdentification":"fff",
            "usedTime":"1000",
            "presentStatueId":"1",
            "picture":"http://wwww"
        }
        }

+ Response 200
+ Response 400

        {
        "data": {
            "msg": "主设备ID不允许为空",
            "code": 400
        }
        }

### 查询指定设备 [GET] /specificequip/{id}
+ Description
    + [MUST] authenticated
+ Response 200

        {
        "data": {
            "id": 26,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-04-22 13:12:38",
            "modified": "2019-04-22 13:12:38",
            "equipmentNo": 10012,
            "loctionId": 12,
            "equipmentId": 222,
            "ip": "192.168.1.1",
            "port": 8080,
            "uniqueIdentification": "fff",
            "usedTime": 1000,
            "presentStatueId": 1,
            "picture": "http://wwww"
        }
        }
### 查询会议室ID查询指定设备列表 [GET] /locations/getSpecificEquipByLocationId/{locationId}
+ Description
    + [MUST] authenticated

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[equipmentListId]  主设备ID  -非必填
    + filter[equipmentListName] 主设备名字 -非必填
    + filter[equipmentCategoryName] (String)  设备分类名称  -非必填（模糊查询）

    
+ Response 200

        {
        "meta": {
            "totalPages": 3,
            "totalElements": 25,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": false,
            "sort": null
        },
        "links": {
            "self": "/equipmentlist?page[number]=1&page[size]=10",
            "first": "/equipmentlist?page[number]=1&page[size]=10",
            "next": "/equipmentlist?page[number]=2&page[size]=10",
            "last": "/equipmentlist?page[number]=3&page[size]=10"
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
            "loctionId": 3,
            "equipmentId": 1,
            "presentStatueId": 1,
            "meetingRoom": "八层大会议室",
            "categoryName": "灯控制器"
        },
        {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "modified": "2019-04-16 13:34:00",
            "equipmentNo": 1002,
            "name": "主席台返看显示器",
            "loctionId": 3,
            "equipmentId": 2,
            "presentStatueId": 1,
            "meetingRoom": "八层大会议室",
            "categoryName": "显示器"
        },
        {
            "id": 3,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "modified": "2019-04-16 13:41:55",
            "equipmentNo": 1003,
            "name": "矩阵切换器",
            "loctionId": 3,
            "equipmentId": 3,
            "presentStatueId": 1,
            "meetingRoom": "八层大会议室",
            "categoryName": "矩阵切换器"
        },
        {
            "id": 4,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "modified": "2019-04-16 14:25:37",
            "equipmentNo": 1004,
            "name": "120寸投影幕（16:10）",
            "loctionId": 6,
            "equipmentId": 9,
            "presentStatueId": 1,
            "meetingRoom": "八层大会议室",
            "categoryName": "投影幕"
        },
        {
            "id": 5,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1005,
            "name": "高清投影机",
            "loctionId": 6,
            "equipmentId": 4,
            "meetingRoom": "八层大会议室",
            "categoryName": "投影机"
        },
        {
            "id": 6,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1006,
            "name": "会议平板",
            "loctionId": 6,
            "equipmentId": 8,
            "meetingRoom": "八层大会议室",
            "categoryName": "平板"
        },
        {
            "id": 7,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1007,
            "name": "数字音频处理器",
            "loctionId": 6,
            "equipmentId": 5,
            "meetingRoom": "八层大会议室",
            "categoryName": "数字音频处理器"
        },
        {
            "id": 8,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1008,
            "name": "会议平板",
            "loctionId": 5,
            "equipmentId": 8,
            "meetingRoom": "八层大会议室",
            "categoryName": "平板"
        },
        {
            "id": 9,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1009,
            "name": "数字音频处理器",
            "loctionId": 5,
            "equipmentId": 5,
            "meetingRoom": "八层大会议室",
            "categoryName": "数字音频处理器"
        },
        {
            "id": 10,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "equipmentNo": 1010,
            "name": "会议平板",
            "loctionId": 7,
            "equipmentId": 8,
            "meetingRoom": "八层大会议室",
            "categoryName": "平板"
        }
        ]
        }

## 品牌管理
+ Data
    + id (int) ID
    + brandName (String) 品牌名字
    + brandLogo (String) 品牌logo
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 新增品牌 [POST] /brand

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)

        {
        "data": {
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "brandName": "111",
            "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
        }
        }
+ Response 200

        {
        "data": {
            "id": 11,
            "type": "Brand"
        }
        }
+ Response 400

        {
        "data": {
            "msg": "品牌名不允许为空",
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

### 删除品牌 [DEL]  /brand

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 200  

### 修改品牌 [PATCH]  /brand/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
        {
        "data": {
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "brandName": "Leviton1",
            "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
        }
        }

+ Response 200
+ Response 400

        {
        "data": {
            "msg": "品牌名不允许为空",
            "code": 400
        }
        }

### 查询品牌 [GET]  /brand/{id}

+ Description
    
+ Response 200

        {
        "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "brandName": "Leviton",
            "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
        }
        }

### 查询品牌列表 [GET]  /brand

+ Description
    
+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填

+ Response 200

        {
        "meta": {
            "totalPages": 1,
            "totalElements": 9,
            "size": 10,
            "number": 1,
            "numberOfElements": 9,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/brand?page[number]=1&page[size]=10",
            "first": "/brand?page[number]=1&page[size]=10",
            "last": "/brand?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "brandName": "Leviton",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 13:08:49",
                "modified": "2019-07-03 13:08:51",
                "brandName": "SAMSUNG",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "brandName": "EXTRON",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "brandName": "BENQ",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "brandName": "NEC",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 6,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 14:17:55",
                "modified": "2019-07-03 14:17:52",
                "brandName": "MAXHUB",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 7,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 14:17:48",
                "modified": "2019-07-03 14:17:45",
                "brandName": "GORSEE",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 8,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 14:17:39",
                "modified": "2019-07-03 14:17:42",
                "brandName": "AMX",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            },
            {
                "id": 9,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-07-03 14:17:32",
                "modified": "2019-07-03 14:17:36",
                "brandName": "AMX1",
                "brandLogo": "https://static.mifanxing.com/yyren/image/113/28/1864145.jpg?w=200&h=90"
            }
        ]
        }

###  通过名字查询品牌 [GET] /brand/getbrandbyname

+ Description
    
+ Parameters
    + brandName (String)  品牌名（也可以不全）  -必填
+ Response 200

            {
            "data": [
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

    
