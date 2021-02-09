# strapi-provider-upload-tencent-cloud-cos

## 参数

| 参数名     | 类型   | 是否必填 | 默认值                                     | 描述                                                                                               |
| ---------- | ------ | -------- | ------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| SecretId   | string | 是       | -                                          | 用户的 SecretId                                                                                    |
| SecretKey  | string | 是       | -                                          | 用户的 SecretKey，建议只在前端调试时使用，避免暴露密钥                                             |
| Region     | string | 是       | -                                          | 存储桶所在地域，枚举值请参见 [地域和访问域名](https://cloud.tencent.com/document/product/436/6224) |
| Bucket     | string | 是       | -                                          | 存储桶的名称，命名规则为 BucketName-APPID，此处填写的存储桶名称必须为此格式                        |
| BasePath   | string | 否       | /                                          | 默认上传的文件夹路径                                                                               |
| BaseOrigin | string | 否       | https://{Bucket}.cos.{Region}.myqcloud.com | 可填入 CDN 根路径                                                                                  |

## 示例

`./config/plugins.js`

```js
module.exports = ({ env }) => ({
  // ...
  upload: {
    provider: env("UPLOAD_PROVIDER", "tencent-cloud-cos"),
    providerOptions: {
      SecretId: env("COS_SECRET_ID"),
      SecretKey: env("COS_SECRET_KEY"),
      Region: env("COS_REGION"),
      Bucket: env("COS_BUCKET"),
      BasePath: env("COS_BASE_PATH", "/"),
      BaseOrigin: env("COS_BASE_ORIGIN", "https://yourdomain.com"),
    },
  },
  // ...
});
```
