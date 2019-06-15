# MFIOT管理端接口文档

+ 2019年6月03日
    + 图片上传接口

+ 2019年6月03日
    + 新增品牌
    + 删除品牌
    + 修改品牌
    + 查询品牌
    + 查询品牌列表

+ 2019年6月03日
    + 新增分类
    + 删除分类
    + 修改分类
    + 查询分类
    + 查询分类列表
    
+ 2019年6月05日
    + 新增设备详情
    + 删除设备详情
    + 修改设备详情
    + 查询设备详情
    + 查询设备列表
    + 受控设备统计接口

+ 2019年6月10日
    + 新增位置
    + 删除位置
    + 修改位置
    + 查询位置
    + 查询位置列表
    + 得到楼层
    + 根据楼层得到会议室

+ 2019年6月10日
    + 新增实际设备
    + 删除实际设备
    + 修改实际设备
    + 查询实际设备
    + 查询实际设备列表
    
+ 2019年6月15日
    + 设备异常个数接口  
    + 受控设备分类统计接口
    + 会议室，受控，中控设备汇总接口
    + 空气质量接口
    + 办公室概况
    + 设备总览


## 图片上传
### 图片上传接口 [POST] /front/upload/image

+ Description


+ Request (application/json)
        上传文件即可
        
+ Response 200

        {
        "data": "/extronpic/7adf829ed2c587baefe4891533d42ec5.jpg"
        }
+ Response 403   

         {
        "data": {
            "msg": "文件类型错误",
            "code": 403
        }
        }
+ Response 400  

         {
        "data": {
            "msg": "bad请求",
            "code": 400
        }
        }


## 品牌管理
+ Data
    + brand_name (String)  品牌名称
    + brand_logo (String) 品牌logo
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    
### 新增品牌  [POST] /front/api/brand/

+ Description

+ Request (application/json)

        {
        "brand_name": "test11",
        "brand_logo": "test11",
        "enabled": 1
        }
+ Response 200

        {
        "id": 101,
        "brand_name": "test",
        "brand_logo": "test11",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-13T10:24:16.076622+08:00",
        "modified": "2019-06-13T10:24:16.077622+08:00"
        }
+ Response 400

        {
        "brand_name": [
            "This field may not be blank."
        ]
        }
        
### 删除品牌 [DEL] /front/api/brand/{id}/

+ Description

+ Response 204 
+ Response 404

        {
        "detail": "Not found."
        }
        

### 修改品牌 [PATCH] /front/api/brand/{id}/

+ Description
+ Request (application/json)
    
        {
        "brand_name": "```1222111",
        "brand_logo": "test11"
        }

+ Response 200

        {
        "id": 13,
        "brand_name": "```1222111",
        "brand_logo": "test11",
        "enabled": 1,
        "creator": 1,
        "modifier": 1,
        "created": "2019-01-01T12:12:00+08:00",
        "modified": "2019-01-01T12:12:00+08:00"
        }

+ Response 404

        {
        "detail": "Not found."
        }

### 查询品牌 [GET] /front/api/brand/{id}/
+ Description
+ Response 200

        {
        "id": 1,
        "brand_name": "ev22i",
        "brand_logo": "www.baidu.com12",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-05-31T21:33:07+08:00",
        "modified": "2019-05-31T21:33:09+08:00"
    }
    
### 查询品牌列表 [GET] /front/page/brand/
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + + size (int)   页尺 -非必填 默认1000
    + brandname (String) 品牌名字 -模糊查询 -非必填
    

+ Response 200

        {
        "totalElements": 13,
        "totalPages": 2,
        "size": 10,
        "first": "http://127.0.0.1:8000/front/page/brand/?page=1",
        "last": "http://127.0.0.1:8000/front/page/brand/?page=2",
        "next": "http://127.0.0.1:8000/front/page/brand/?page=2",
        "previous": null,
        "results": [
            {
                "id": 1,
                "brand_name": "ev22i",
                "brand_logo": "www.baidu.com12",
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-31T21:33:07+08:00",
                "modified": "2019-05-31T21:33:09+08:00"
            },
            {
                "id": 2,
                "brand_name": "ev22i2",
                "brand_logo": "111",
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": null,
                "modified": null
            },
            {
                "id": 3,
                "brand_name": "test1",
                "brand_logo": "111",
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-06-04T12:12:00+08:00",
                "modified": "2019-06-04T12:22:00+08:00"
            },
            {
                "id": 4,
                "brand_name": "eeee",
                "brand_logo": "1111",
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": null,
                "modified": null
            },
            {
                "id": 10,
                "brand_name": "sfsdf",
                "brand_logo": "sdfsdf",
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": null,
                "modified": null
            }
        ]
        }


## 分类管理
+ Data
    + category_name (String)  分类名称
    + category_description (String) 分类描述
    + category_pic  (String) 分类图片
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    
### 新增分类  [POST] /front/api/equipmentcategory/

+ Description

+ Request (application/json)

        {
        "category_name": "音响2",
        "category_description": "音响",
        "category_pic": "www",
        "enabled": 1
        }
+ Response 200

        {
        "id": 2,
        "category_name": "音响2",
        "category_description": "音响",
        "category_pic": "www",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:49:21+08:00",
        "modified": "2019-06-04T18:49:25+08:00"
        }
+ Response 400

        {
        "category_name": [
            "This field may not be blank."
        ]
        }
        
### 删除分类 [DEL] /front/api/equipmentcategory/{id}/

+ Description

+ Response 204 
+ Response 404

        {
        "detail": "Not found."
        }
        

### 修改分类 [PATCH] /front/api/equipmentcategory/{id}/

+ Description
+ Request (application/json)
    
        {
        "category_name": "333311113",
        "category_description": "音响",
        "category_pic": "www"
        }

+ Response 200

        {
        "id": 3,
        "category_name": "333311113",
        "category_description": "音响",
        "category_pic": "www",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:49:21+08:00",
        "modified": "2019-06-04T18:49:25+08:00"
        }

+ Response 404

        {
        "detail": "Not found."
        }

### 查询分类 [GET] /front/api/equipmentcategory/{id}/
+ Description
+ Response 200

        {
        "id": 3,
        "category_name": "333311113",
        "category_description": "音响",
        "category_pic": "www",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:49:21+08:00",
        "modified": "2019-06-04T18:49:25+08:00"
        }
    
### 查询分类列表 [GET] /front/page/equipmentcategory/
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + size (int)   页尺 -非必填 默认1000
    + categoryname (String) 分类名称  -非必填模糊查询

+ Response 200

        {
        "totalElements": 2,
        "totalPages": 1,
        "size": 10,
        "first": "http://127.0.0.1:8000/front/page/equipmentcategory/?page=1",
        "last": "http://127.0.0.1:8000/front/page/equipmentcategory/?page=1",
        "next": null,
        "previous": null,
        "results": [
            {
                "id": 1,
                "category_name": "音响",
                "category_description": "音响",
                "category_pic": "www",
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-06-04T18:49:21+08:00",
                "modified": "2019-06-04T18:49:25+08:00"
            },
            {
                "id": 3,
                "category_name": "333311113",
                "category_description": "音响",
                "category_pic": "www",
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-06-04T18:49:21+08:00",
                "modified": "2019-06-04T18:49:25+08:00"
            }
        ]
        }



## 设备详情管理
+ Data
    + id (int) id
    + equipment_name (String)  设备名称
    + equipment_pic (String)  设备图片
    + brand (int) 品牌ID
    + brand_name  (String) 品牌名字
    + brand_logo (String) 品牌logo
    + equipment_category (int) 设备分类id
    + equipment_category_name (String) 设备分类名字
    + equipment_category_pic (String) 设备分类图片
    + model  (String) 设备型号
    + quipmente_amount (int)  实际设备其引用次数
    + description (String) 描述
    + iscontrolled (int) 是否是受控设备 1为受控设备  0为非受控设备
    + lifetime (int) 寿命时长（单位分钟）
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    
    
### 新增设备详情  [POST] /front/api/equipmentdetails/

+ Description

+ Request (application/json)

        {
        "equipment_name": "快思聪中控",
        "equipment_pic": "www.baid.com",
        "model": "11",
        "description": "111",
        "iscontrolled": 1,
        "lifetime": 0,
        "enabled": 1,
        "brand": 1,
        "equipment_category": 1
        }
+ Response 200

        {
        "id": 26,
        "equipment_name": "快思聪中控",
        "equipment_pic": "www.baid.com",
        "brand": 1,
        "brand_name": "ev22i",
        "brand_logo": "www.baidu.com12",
        "equipment_category": 1,
        "equipment_category_name": "音响",
        "equipment_category_pic": "www",
        "model": "11",
        "description": "111",
        "iscontrolled": 1,
        "lifetime": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00"
        }
+ Response 400

        {
        "equipment_name": [
            "This field may not be blank."
        ]
        }
+ Response 404
    
        {
        "detail": "Not found."
        }
        
### 删除设备详情 [DEL] /front/api/equipmentdetails/{id}/

+ Description

+ Response 204 
+ Response 404

        {
        "detail": "Not found."
        }
        

### 修改设备详情 [PATCH] /front/api/equipmentdetails/{id}/

+ Description
+ Request (application/json)
    
        {
        "equipment_name": "快思聪中控24",
        "equipment_pic": "www.baid.com",
        "model": "1124",
        "description": "11124",
        "iscontrolled": 1,
        "lifetime": 0,
        "brand": 1,
        "equipment_category": 1
        }

+ Response 200

        {
        "id": 24,
        "equipment_name": "快思聪中控24",
        "equipment_pic": "www.baid.com",
        "brand": 1,
        "brand_name": "ev22i",
        "brand_logo": "www.baidu.com12",
        "equipment_category": 1,
        "equipment_category_name": "音响",
        "equipment_category_pic": "www",
        "model": "1124",
        "description": "11124",
        "iscontrolled": 1,
        "lifetime": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00"
        }

+ Response 404

        {
        "detail": "Not found."
        }

### 查询设备详情 [GET] /front/api/equipmentdetails/{id}/
+ Description
+ Response 200

        {
        "id": 26,
        "equipment_name": "快思聪中控",
        "equipment_pic": "www.baid.com",
        "brand": 1,
        "brand_name": "ev22i",
        "brand_logo": "www.baidu.com12",
        "equipment_category": 1,
        "equipment_category_name": "音响",
        "equipment_category_pic": "www",
        "model": "11",
        "description": "111",
        "iscontrolled": 1,
        "lifetime": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00"
        }
    
### 查询设备列表 [GET] /front/page/equipmentdetails/
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + size (int)   页尺 -非必填 默认1000
    + equipmentname (String) 设备名称 -非必填
    + model (String) 型号  -非必填

+ Response 200

        {
        "totalElements": 42,
        "totalPages": 21,
        "size": 2,
        "first": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=1&size=2",
        "last": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=21&size=2",
        "next": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=2&size=2",
        "previous": null,
        "results": [
        {
            "id": 1,
            "equipment_name": "鹅颈电容传声器",
            "equipment_pic": "pic",
            "brand": 1,
            "brand_name": "SENNHEISER",
            "brand_logo": "http://static.mifanxing.com/yyren/image/107/28/1862592.jpg?w=200&h=90",
            "equipment_category": 1,
            "equipment_category_name": "音频系统",
            "equipment_category_pic": "www图",
            "model": "MEG 14-40-L-II ",
            "quipmente_amount": 1,
            "description": "extron001",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00"
        },
        {
            "id": 2,
            "equipment_name": "无线手持话筒套装",
            "equipment_pic": "www.baid.com",
            "brand": 1,
            "brand_name": "SENNHEISER",
            "brand_logo": "http://static.mifanxing.com/yyren/image/107/28/1862592.jpg?w=200&h=90",
            "equipment_category": 1,
            "equipment_category_name": "音频系统",
            "equipment_category_pic": "www图",
            "model": "SL HANDHELD SET DW",
            "quipmente_amount": 1,
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00"
        }
        ]
        }


### 受控设备统计接口 [GET] /front/page/equipmentdetails/?iscontrolled=1
+ Description

+ Parameters
  
+ Response 200

        {
        "totalElements": 42,
        "totalPages": 21,
        "size": 2,
        "first": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=1&size=2",
        "last": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=21&size=2",
        "next": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=2&size=2",
        "previous": null,
        "results": [
        {
            "id": 1,
            "equipment_name": "鹅颈电容传声器",
            "equipment_pic": "pic",
            "brand": 1,
            "brand_name": "SENNHEISER",
            "brand_logo": "http://static.mifanxing.com/yyren/image/107/28/1862592.jpg?w=200&h=90",
            "equipment_category": 1,
            "equipment_category_name": "音频系统",
            "equipment_category_pic": "www图",
            "model": "MEG 14-40-L-II ",
            "quipmente_amount": 1,
            "description": "extron001",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00"
        },
        {
            "id": 2,
            "equipment_name": "无线手持话筒套装",
            "equipment_pic": "www.baid.com",
            "brand": 1,
            "brand_name": "SENNHEISER",
            "brand_logo": "http://static.mifanxing.com/yyren/image/107/28/1862592.jpg?w=200&h=90",
            "equipment_category": 1,
            "equipment_category_name": "音频系统",
            "equipment_category_pic": "www图",
            "model": "SL HANDHELD SET DW",
            "quipmente_amount": 1,
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00"
        }
        ]
        }





## 位置管理
+ Data
    + id (int) id
    + parent_id (int) 父ID
    + location_name (String)  位置名称
    + location_no (String)  位置编号
    + description (String) 描述
    + location_pic (String) 位置图片
    + leaf (int)  是否叶子节点 1为叶子节点  0为非叶子节点
    + x_axis (float) X坐标
    + y_axis (float) Y坐标
    + status (int) 1正常  0不正常（装修等原因停止使用）
    + isconference (int)  1为是会议室  0为非会议室
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    
    
### 新增位置节点  [POST] /front/api/location/

+ Description

+ Request (application/json)

        {
        "parent_id": 1,
        "location_name": "二层会议室",
        "location_no": 1006,
        "description": "二层会议室",
        "location_pic": null,
        "leaf": 0,
        "x_axis": 66,
        "y_axis": 44,
        "status": 1,
        "isconference": 0
        }
+ Response 200

        {
        "id": 10,
        "parent_id": 1,
        "location_name": "二层会议室",
        "location_no": 1006,
        "description": "二层会议室",
        "location_pic": null,
        "leaf": 0,
        "x_axis": 66,
        "y_axis": 44,
        "status": 1,
        "isconference": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:09:53+08:00",
        "modified": "2019-06-10T19:09:55+08:00"
        }
+ Response 400

        {
        "location_name": [
            "This field may not be blank."
        ]
        }
+ Response 404
    
        {
        "detail": "Not found."
        }
        
### 删除位置 [DEL] /front/api/location/{id}/

+ Description

+ Response 204 
+ Response 404

        {
        "detail": "Not found."
        }
        

### 修改位置节点 [PATCH] /front/api/location/{id}/

+ Description
+ Request (application/json)
    
        {
        "parent_id": 1,
        "location_name": "1222",
        "location_no": 1006,
        "description": "二层会议室",
        "location_pic": null,
        "leaf": 0,
        "x_axis": 66,
        "y_axis": 44,
        "status": 1,
        "isconference": 0,
        "enabled": 1
        }

+ Response 200

        {
        "id": 12,
        "parent_id": 1,
        "location_name": "1222",
        "location_no": 1006,
        "description": "二层会议室",
        "location_pic": null,
        "leaf": 0,
        "x_axis": 66,
        "y_axis": 44,
        "status": 1,
        "isconference": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:09:53+08:00",
        "modified": "2019-06-10T19:09:55+08:00"
        }

+ Response 404

        {
        "detail": "Not found."
        }

### 查询位置节点 [GET] /front/api/location/{id}/
+ Description
+ Response 200

        {
        "id": 12,
        "parent_id": 1,
        "location_name": "1222",
        "location_no": 1006,
        "description": "二层会议室",
        "location_pic": null,
        "leaf": 0,
        "x_axis": 66,
        "y_axis": 44,
        "status": 1,
        "isconference": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:09:53+08:00",
        "modified": "2019-06-10T19:09:55+08:00"
        }
+ Response 404
        
        {
        "detail": "Not found."
        }
  
  
### 查询位置列表 [GET] /front/page/location/
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + size (int)   页尺 -非必填 默认1000
    + locationname (String) 位置名称模糊查询
    + isconference (int) 是否会议室 1是 0不是
    + leaf (int) 是否叶子节点 1是 0不是

+ Response 200

        {
        "totalElements": 12,
        "totalPages": 2,
        "size": 10,
        "first": "http://127.0.0.1:8000/front/page/location/?page=1",
        "last": "http://127.0.0.1:8000/front/page/location/?page=2",
        "next": null,
        "previous": "http://127.0.0.1:8000/front/page/location/",
        "results": [
        {
            "id": 11,
            "parent_id": 1,
            "location_name": "二层会议室",
            "location_no": 1006,
            "description": "二层会议室",
            "location_pic": null,
            "leaf": 0,
            "x_axis": 66,
            "y_axis": 44,
            "status": 1,
            "isconference": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-10T19:09:53+08:00",
            "modified": "2019-06-10T19:09:55+08:00"
        },
        {
            "id": 12,
            "parent_id": 1,
            "location_name": "1222",
            "location_no": 1006,
            "description": "二层会议室",
            "location_pic": null,
            "leaf": 0,
            "x_axis": 66,
            "y_axis": 44,
            "status": 1,
            "isconference": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-10T19:09:53+08:00",
            "modified": "2019-06-10T19:09:55+08:00"
        }
    ]
    }
    
### 得到楼层 [GET] /front/getfloor/?isfloor=1

+ Response 200
    
        {
        "results": [
        {
            "id": 13,
            "location_name": "一层"
        },
        {
            "id": 14,
            "location_name": "8层"
        }
        ]
        }

### 根据楼层得到会议室 [GET] /front/getfloor/?isconference=1

+ Parameters
    + parentid (int)  楼层id  -必填
    + isconference (int)  是否会议室1为会议室 0为非会议室

+ Response 200

        {
        "results": [
        {
            "id": 2,
            "location_name": "一层会议室A"
        },
        {
            "id": 3,
            "location_name": "一层会议室B"
        },
        {
            "id": 4,
            "location_name": "一层会议室C"
        }
        ]
        }
    

## 实际设备管理
+ Data
    + id (int) id
    + loucengid  (int) 楼层id
    + louchengname (String) 楼层名字
    + equipment_no (String)  设备编号
    + equipment (int)  设备id
    + equipment_name (String)  设备名字
    + equipment_pic (String) 设备图片
    + location (int)  位置ID
    + location_name (String) 位置名字
    + brandid (int) 品牌id
    + brandname (String)  品牌名字
    + categoryid (int) 分类id
    + categoryname (String)  分类名字
    + model (String)
    + ip (String)  ip
    + port (int)   端口
    + service_time (int) 服务时长
    + used_no  (int)
    + failure_no (int)
    + status (int)   1为正常 0为关闭  2为故障
    + ismonitor (int)  是否作为监控设备 1为是  0为不是
    + x_axis (float)  X轴
    + y_axis (float)  Y轴
    + unique_id (String)   唯一ID
    + equipment (int) 
    + equipment_name (String) 设备名称
    + location (int) 
    + location_name (String) 位置名称
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    
    
### 新增设备详情  [POST] /front/api/equipmentdetails/

+ Description

+ Request (application/json)

        {
        "equipment_no": 200022222,
        "ip": "192.168.2.22",
        "port": 8081,
        "service_time": 15,
        "status": 1,
        "ismonitor": 1,
        "x_axis": 222,
        "y_axis": 333,
        "unique_id": "sn-2",
        "enabled": 1
        "equipment": 2,
        "location": 3
        }
+ Response 200

        {
        "id": 1,
        "equipment_no": 20001,
        "equipment": 1,
        "equipment_name": "ss",
        "location": 2,
        "location_name": "一层会议室",
        "ip": "192.168.1.22",
        "port": 8008,
        "service_time": 15,
        "status": 1,
        "ismonitor": 0,
        "x_axis": 22,
        "y_axis": 56,
        "unique_id": "sn-1",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:55:32+08:00",
        "modified": "2019-06-10T19:55:35+08:00"
        }
+ Response 400

        {
        "equipment_name": [
            "This field may not be blank."
        ]
        }
+ Response 404
    
        {
        "detail": "Not found."
        }
        
### 删除设备详情 [DEL] /front/api/realityequipment/{id}/

+ Description

+ Response 204 
+ Response 404

        {
        "detail": "Not found."
        }
        

### 修改实际设备 [PATCH] /front/api/realityequipment/{id}/

+ Description
+ Request (application/json)
    
        {
        "equipment_no": 200022222,
        "ip": "192.168.2.22",
        "port": 8081,
        "service_time": 15,
        "status": 1,
        "ismonitor": 1,
        "x_axis": 222,
        "y_axis": 333,
        "unique_id": "sn-2",
        "enabled": 1,
        "equipment": 2,
        "location": 3
        }

+ Response 200

        {
        "id": 2,
        "equipment_no": 200022222,
        "equipment": 1,
        "equipment_name": "ss",
        "location": 2,
        "location_name": "一层会议室",
        "ip": "192.168.2.22",
        "port": 8081,
        "service_time": 15,
        "status": 1,
        "ismonitor": 1,
        "x_axis": 222,
        "y_axis": 333,
        "unique_id": "sn-2",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:56:25+08:00",
        "modified": "2019-06-10T19:56:29+08:00",
        }

+ Response 404

        {
        "detail": "Not found."
        }

### 查询实际设备 [GET] /front/api/realityequipment/{id}/
+ Description
+ Response 200

        {
        "id": 1,
        "loucengid": 6,
        "louchengname": "六层",
        "equipment_no": 2001,
        "equipment": 28,
        "equipment_name": "占用感应器",
        "equipment_pic": null,
        "location": 8,
        "location_name": "男厕坑位1",
        "brandid": 2,
        "brandname": "Extron",
        "categoryid": 11,
        "categoryname": "传感器",
        "model": "OCS 100C",
        "ip": "",
        "port": null,
        "service_time": 15,
        "used_no": 0,
        "failure_no": 0,
        "status": 1,
        "ismonitor": 0,
        "x_axis": null,
        "y_axis": null,
        "unique_id": "",
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:55:32+08:00",
        "modified": "2019-06-10T19:55:35+08:00"
        }
    
### 查询实际设备列表 [GET] /front/page/realityequipment/
例如：http://127.0.0.1:8000/front/page/realityequipment/?brandids=1,2&categoryids=&page=1&size=2
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + size (int)   页尺 -非必填 默认1000
    + ismonitor  (int) 1为监控设备 0为非监控设备
    + brandids (String) 品牌ids -非必填
    + categoryids (String) 分类ids -非必填
    + localids (String) 位置ids -非必填
    + status (int)  状态 1为正常 0为关闭  2为故障

+ Response 200

        {
        "totalElements": 15,
        "totalPages": 8,
        "size": 2,
        "first": "http://127.0.0.1:8000/front/page/realityequipment/?brandids=1%2C2&categoryids=&localids=5&page=1&size=2",
        "last": "http://127.0.0.1:8000/front/page/realityequipment/?brandids=1%2C2&categoryids=&localids=5&page=8&size=2",
        "next": "http://127.0.0.1:8000/front/page/realityequipment/?brandids=1%2C2&categoryids=&localids=5&page=2&size=2",
        "previous": null,
        "results": [
            {
            "id": 10,
            "loucengid": 2,
            "louchengname": "六层",
            "equipment_no": 2010,
            "equipment": 1,
            "equipment_name": "鹅颈电容传声器",
            "location": 5,
            "location_name": "中会议室",
            "brandid": 1,
            "brandname": "SENNHEISER",
            "categoryid": 1,
            "categoryname": "音频系统",
            "equipmentpic": "pic",
            "model": "MEG 14-40-L-II ",
            "ip": null,
            "port": null,
            "service_time": 0,
            "status": 0,
            "ismonitor": 0,
            "x_axis": null,
            "y_axis": null,
            "unique_id": null,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": null,
            "modified": null
            },
            {
            "id": 11,
            "loucengid": 2,
            "louchengname": "六层",
            "equipment_no": 2011,
            "equipment": 2,
            "equipment_name": "无线手持话筒套装",
            "location": 5,
            "location_name": "中会议室",
            "brandid": 1,
            "brandname": "SENNHEISER",
            "categoryid": 1,
            "categoryname": "音频系统",
            "equipmentpic": "www.baid.com",
            "model": "SL HANDHELD SET DW",
            "ip": null,
            "port": null,
            "service_time": 0,
            "status": 0,
            "ismonitor": 0,
            "x_axis": null,
            "y_axis": null,
            "unique_id": null,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": null,
            "modified": null
            }
            ]
            }
### 设备异常个数接口 [GET] /front/geteqiupmentcount/
+ Data
    + status (int) 状态id(1为正常 0为关闭 2为故障)
    + realityequipmentcount  (int) 设备数
+ Description

+ Parameters
    + status (int)  状态 1为正常 0为关闭 2为故障(默认是故障状态)

+ Response 200

        {
        "data": {
            "status": "0",
            "realityequipmentcount": 48
        }
        }
    
### 受控设备分类统计接口 [GET] /front/equipmentstatistics/
+ Data
    + sumcount (int) 受控设备总数
    + id  (int) id
    + category_name (String) 分类名字
    + count (int) 受控设备数
    + percent (float) 受控设备占比
+ Description

+ Parameters
+ Response 200

            {
            "data": {
                "sumcount": 43,
                "results": [
                    {
                    "id": 1,
                    "category_name": "音频设备",
                    "count": 19,
                    "percent": 44.19
                },
                {
                    "id": 2,
                    "category_name": "视频设备",
                    "count": 4,
                    "percent": 9.3
                },
                {
                    "id": 3,
                    "category_name": "中控设备",
                    "count": 0,
                    "percent": 0
                },
                {
                    "id": 4,
                    "category_name": "其他设备",
                    "count": 0,
                    "percent": 0
                },
                {
                    "id": 5,
                    "category_name": "照明设备",
                    "count": 5,
                    "percent": 11.63
                },
                {
                    "id": 8,
                    "category_name": "温控设备",
                    "count": 0,
                    "percent": 0
                },
                {
                    "id": 11,
                    "category_name": "传感器",
                    "count": 15,
                    "percent": 34.88
                },
                {
                    "id": 13,
                    "category_name": "网络设备",
                    "count": 0,
                    "percent": 0
                }
        ]
    }
}

### 会议室，受控，中控设备汇总接口 [GET] /front/collect/
+ Data
    + meetingroomsum (int) 会议室数量
    + iscontrolledequipmentsum (int) 受控设备数量
    + controlequipmentsum (int) 中控设备数量
    
+ Description

+ Parameters
+ Response 200

        {
        "data": [
            {
                "meetingroomsum": 3,
                "other": "other"
            },
            {
                "iscontrolledequipmentsum": 43,
                "other": "other"
            },
            {
                "Controlequipmentsum": 1,
                "other": "other"
            }
        ]
        }

### 空气质量接口 [GET] /front/environmental/?locationid=5
+ Data
    + id (int) 会议室数量
    + temperature (int) 温度
    + humidity (int) 湿度
    + tvoc (float) tvoc值
    + ch20 (float)  ch20值
    + co2 (float)  co2值
    + pm10 (float) pm10值
    + pm25 (float) pm2.5值
    + methanal  (float) 甲醛值
    + content (String) 日志内容
    + creator (int)  创建人
    + created (Datetime) 日期
    + location (int)  位置id
    
+ Description

+ Parameters
    + locationid (int) 必填 填写位置的id   
+ Response 200

        {
        "id": 3,
        "temperature": 22,
        "humidity": 22,
        "tvoc": 22,
        "ch20": 22,
        "co2": 22,
        "pm10": 22,
        "pm25": 22,
        "methanal": 22,
        "content": null,
        "creator": 0,
        "created": "2019-06-15T15:58:25Z",
        "location": 5
        }
        
### 办公室概况 [GET] /front/meetingsituation/
+ Data
    + meetingroomsum (int) 会议室总数
    + id  (int) id
    + category_name (String) 分类名字
    + count (int) 受控设备数
    + percent (float) 受控设备占比
    
+ Description
+ Parameters
    +   
+ Response 200

            {
            "data": {
            "meetingroomsum": 3,
            "results": [
                {
                    "id": 1,
                    "category_name": "音频设备",
                    "count": 19,
                    "percent": 43.18
                },
                {
                    "id": 2,
                    "category_name": "视频设备",
                    "count": 4,
                    "percent": 9.09
                },
                {
                    "id": 3,
                    "category_name": "中控设备",
                    "count": 1,
                    "percent": 2.27
                },
                {
                    "id": 4,
                    "category_name": "其他设备",
                    "count": 0,
                    "percent": 0
                },
                {
                    "id": 5,
                    "category_name": "照明设备",
                    "count": 5,
                    "percent": 11.36
                },
                {
                    "id": 8,
                    "category_name": "温控设备",
                    "count": 0,
                    "percent": 0
                },
                {
                    "id": 11,
                    "category_name": "传感器",
                    "count": 15,
                    "percent": 34.09
                },
                {
                    "id": 13,
                    "category_name": "网络设备",
                    "count": 0,
                    "percent": 0
                }
            ]
        }
        }
### 设备总览
+ Data
    + equipmentsum (int) 设备总数
    + workingequipmentsum  (int) 正在工作设备数
    + faultequipmentsum (int) 故障设备数
+ Description
+ Parameters
    + locationid (int) 位置id 必填
+ Response 200

        {
        "data": [
            {
                "equipmentsum": 28
            },
            {
                "workingequipmentsum": 2
            },
            {
                "faultequipmentsum": 0
            }
            ]
            }
        
+ Response 400

        {
        "data": {
            "msg": "not data",
            "code": 400
        }
        }
