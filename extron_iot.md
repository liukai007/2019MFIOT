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

+ 2019年6月10日
    + 新增位置
    + 删除位置
    + 修改位置
    + 查询位置
    + 查询位置列表

+ 2019年6月10日
    + 新增实际设备
    + 删除实际设备
    + 修改实际设备
    + 查询实际设备
    + 查询实际设备列表

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
            "brand_name": "test",
            "brand_logo": "test11",
            "enabled": 1,
            "creator": 1,
            "modifier": 1,
            "created": "2019-01-01 12:12",
            "modified": "2019-01-01 12:12"
        }
+ Response 200

        {
            "id": 15,
            "brand_name": "test",
            "brand_logo": "test11",
            "enabled": 1,
            "creator": 1,
            "modifier": 1,
            "created": "2019-01-01T12:12:00+08:00",
            "modified": "2019-01-01T12:12:00+08:00"
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
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:49:21+08:00",
        "modified": "2019-06-04T18:49:25+08:00"
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
    + equipment_category (int) 设备分类id
    + model  (String) 设备型号
    + description (String) 描述
    + iscontrolled (int) 是否是受控设备 1为受控设备  0为非受控设备
    + lifetime (int) 寿命时长（单位秒）
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
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00",
        "brand": 1,
        "equipment_category": 1
        }
+ Response 200

        {
        "id": 24,
        "equipment_name": "快思聪中控",
        "equipment_pic": "www.baid.com",
        "model": "11",
        "description": "111",
        "iscontrolled": 1,
        "lifetime": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00",
        "brand": 1,
        "equipment_category": 1
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
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00",
        "brand": 1,
        "equipment_category": 1
        }

+ Response 200

        {
        "id": 24,
        "equipment_name": "快思聪中控24",
        "equipment_pic": "www.baid.com",
        "model": "1124",
        "description": "11124",
        "iscontrolled": 1,
        "lifetime": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00",
        "brand": 1,
        "equipment_category": 1
        }

+ Response 404

        {
        "detail": "Not found."
        }

### 查询设备详情 [GET] /front/api/equipmentdetails/{id}/
+ Description
+ Response 200

        {
        "equipment_name": "快思聪中控24",
        "equipment_pic": "www.baid.com",
        "model": "1124",
        "description": "11124",
        "iscontrolled": 1,
        "lifetime": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-04T18:51:28+08:00",
        "modified": "2019-06-04T18:51:34+08:00",
        "brand": 1,
        "equipment_category": 1
        }
    
### 查询设备详情列表 [GET] /front/page/equipmentdetails/
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + size (int)   页尺 -非必填 默认1000

+ Response 200

        {
        "totalElements": 24,
        "totalPages": 3,
        "size": 10,
        "first": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=1",
        "last": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=3",
        "next": "http://127.0.0.1:8000/front/page/equipmentdetails/?page=3",
        "previous": "http://127.0.0.1:8000/front/page/equipmentdetails/",
        "results": [
        {
            "id": 11,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 12,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 13,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 14,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 15,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 16,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 17,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 18,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 19,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
        },
        {
            "id": 20,
            "equipment_name": "快思聪中控",
            "equipment_pic": "www.baid.com",
            "model": "11",
            "description": "111",
            "iscontrolled": 1,
            "lifetime": 0,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-06-04T18:51:28+08:00",
            "modified": "2019-06-04T18:51:34+08:00",
            "brand": 1,
            "equipment_category": 1
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
        "isconference": 0,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:09:53+08:00",
        "modified": "2019-06-10T19:09:55+08:00"
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
        

### 修改设备详情 [PATCH] /front/api/location/{id}/

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
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:09:53+08:00",
        "modified": "2019-06-10T19:09:55+08:00"
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

### 查询设备详情 [GET] /front/api/location/{id}/
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
  
  
### 查询设备详情列表 [GET] /front/page/location/
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + size (int)   页尺 -非必填 默认1000

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



## 实际设备管理
+ Data
    + id (int) id
    + equipment_no (String)  设备编号
    + ip (String)  ip
    + port (int)   端口
    + service_time (int) 服务时长
    + status (int)   1为正常 0为关闭  2为故障
    + ismonitor (int)  是否作为监控设备 1为是  0为不是
    + x_axis (float)  X轴
    + y_axis (float)  Y轴
    + unique_id (String)   唯一ID
    + equipment (int) 
    + location (int) 
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
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:56:25+08:00",
        "modified": "2019-06-10T19:56:29+08:00",
        "equipment": 2,
        "location": 3
        }
+ Response 200

        {
        "id": 3,
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
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:56:25+08:00",
        "modified": "2019-06-10T19:56:29+08:00",
        "equipment": 2,
        "location": 3
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
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:56:25+08:00",
        "modified": "2019-06-10T19:56:29+08:00",
        "equipment": 2,
        "location": 3
        }

+ Response 200

        {
        "id": 2,
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
        "creator": 0,
        "modifier": 0,
        "created": "2019-06-10T19:56:25+08:00",
        "modified": "2019-06-10T19:56:29+08:00",
        "equipment": 2,
        "location": 3
        }

+ Response 404

        {
        "detail": "Not found."
        }

### 查询实际设备 [GET] /front/api/realityequipment/{id}/
+ Description
+ Response 200

        {
        "id": 2,
        "equipment_no": 20002,
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
        "equipment": 2,
        "location": 3
        }
    
### 查询实际设备列表 [GET] /front/page/realityequipment/
+ Description

+ Parameters
    + page (int)  页码  -非必填 默认为1
    + size (int)   页尺 -非必填 默认1000

+ Response 200

       {
        "totalElements": 2,
        "totalPages": 1,
        "size": 10,
        "first": "http://127.0.0.1:8000/front/page/realityequipment/?page=1",
        "last": "http://127.0.0.1:8000/front/page/realityequipment/?page=1",
        "next": null,
        "previous": null,
        "results": [
        {
            "id": 1,
            "equipment_no": 20001,
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
            "modified": "2019-06-10T19:55:35+08:00",
            "equipment": 1,
            "location": 2
        },
        {
            "id": 2,
            "equipment_no": 20002,
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
            "equipment": 2,
            "location": 3
        }
        ]
        }
