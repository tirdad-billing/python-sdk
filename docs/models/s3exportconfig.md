# S3ExportConfig


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `bucket`                                                               | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | S3 bucket name                                                         |
| `compression`                                                          | [Optional[models.S3CompressionType]](../models/s3compressiontype.md)   | :heavy_minus_sign:                                                     | N/A                                                                    |
| `encryption`                                                           | [Optional[models.S3EncryptionType]](../models/s3encryptiontype.md)     | :heavy_minus_sign:                                                     | N/A                                                                    |
| `is_flexprice_managed`                                                 | *Optional[bool]*                                                       | :heavy_minus_sign:                                                     | If true, use Tirdad-managed S3 credentials instead of user-provided |
| `key_prefix`                                                           | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | Optional prefix for S3 keys (e.g., "flexprice-exports/")               |
| `region`                                                               | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | AWS region (e.g., "us-west-2")                                         |