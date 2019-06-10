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
    + 新增设备
    + 新增设备
    + 删除设备
    + 修改设备
    + 查询设备
    + 查询设备列表

+ 2019年6月05日
    + 新增实际设备
    + 删除实际设备
    + 修改实际设备
    + 查询实际设备

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
    
### 查询品牌列表 [GET] /front/page/brand/?page=1
+ Description

+ Parameters
    + page (int)  页码  -非必填

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
    
### 查询分类列表 [GET] /front/page/equipmentcategory/?page=1
+ Description

+ Parameters
    + page (int)  页码  -非必填

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
