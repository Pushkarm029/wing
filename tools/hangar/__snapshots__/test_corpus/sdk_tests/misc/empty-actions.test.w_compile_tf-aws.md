# [empty-actions.test.w](../../../../../../examples/tests/sdk_tests/misc/empty-actions.test.w) | compile | tf-aws

## main.tf.json
```json
{
  "//": {
    "metadata": {
      "backend": "local",
      "stackName": "root",
      "version": "0.17.0"
    },
    "outputs": {
      "root": {
        "Default": {
          "cloud.TestRunner": {
            "TestFunctionArns": "WING_TEST_RUNNER_FUNCTION_IDENTIFIERS"
          }
        }
      }
    }
  },
  "data": {
    "aws_region": {
      "Region": {
        "//": {
          "metadata": {
            "path": "root/Default/Region",
            "uniqueId": "Region"
          }
        }
      }
    }
  },
  "output": {
    "WING_TEST_RUNNER_FUNCTION_IDENTIFIERS": {
      "value": "[]"
    }
  },
  "provider": {
    "aws": [
      {}
    ]
  },
  "resource": {
    "aws_api_gateway_deployment": {
      "cloudApi_api_deployment_545514BF": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/api/deployment",
            "uniqueId": "cloudApi_api_deployment_545514BF"
          }
        },
        "lifecycle": {
          "create_before_destroy": true
        },
        "rest_api_id": "${aws_api_gateway_rest_api.cloudApi_api_2B334D75.id}",
        "triggers": {
          "redeployment": "${sha256(aws_api_gateway_rest_api.cloudApi_api_2B334D75.body)}"
        }
      }
    },
    "aws_api_gateway_rest_api": {
      "cloudApi_api_2B334D75": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/api/api",
            "uniqueId": "cloudApi_api_2B334D75"
          }
        },
        "body": "{\"openapi\":\"3.0.3\",\"paths\":{\"/foo\":{\"get\":{\"operationId\":\"get-foo\",\"responses\":{\"200\":{\"description\":\"200 response\",\"content\":{}}},\"parameters\":[],\"x-amazon-apigateway-integration\":{\"uri\":\"arn:aws:apigateway:${data.aws_region.Region.name}:lambda:path/2015-03-31/functions/${aws_lambda_function.cloudApi_OnRequest0_E65A93DD.arn}/invocations\",\"type\":\"aws_proxy\",\"httpMethod\":\"POST\",\"responses\":{\"default\":{\"statusCode\":\"200\"}},\"passthroughBehavior\":\"when_no_match\",\"contentHandling\":\"CONVERT_TO_TEXT\"}}},\"/bar\":{\"get\":{\"operationId\":\"get-bar\",\"responses\":{\"200\":{\"description\":\"200 response\",\"content\":{}}},\"parameters\":[],\"x-amazon-apigateway-integration\":{\"uri\":\"arn:aws:apigateway:${data.aws_region.Region.name}:lambda:path/2015-03-31/functions/${aws_lambda_function.cloudApi_OnRequest1_3D65B7B4.arn}/invocations\",\"type\":\"aws_proxy\",\"httpMethod\":\"POST\",\"responses\":{\"default\":{\"statusCode\":\"200\"}},\"passthroughBehavior\":\"when_no_match\",\"contentHandling\":\"CONVERT_TO_TEXT\"}}},\"/{proxy+}\":{\"x-amazon-apigateway-any-method\":{\"produces\":[\"application/json\"],\"x-amazon-apigateway-integration\":{\"type\":\"mock\",\"requestTemplates\":{\"application/json\":\"\\n                {\\\"statusCode\\\": 404}\\n              \"},\"passthroughBehavior\":\"never\",\"responses\":{\"404\":{\"statusCode\":\"404\",\"responseParameters\":{\"method.response.header.Content-Type\":\"'application/json'\"},\"responseTemplates\":{\"application/json\":\"{\\\"statusCode\\\": 404, \\\"message\\\": \\\"Error: Resource not found\\\"}\"}},\"default\":{\"statusCode\":\"404\",\"responseParameters\":{\"method.response.header.Content-Type\":\"'application/json'\"},\"responseTemplates\":{\"application/json\":\"{\\\"statusCode\\\": 404, \\\"message\\\": \\\"Error: Resource not found\\\"}\"}}}},\"responses\":{\"404\":{\"description\":\"404 response\",\"headers\":{\"Content-Type\":{\"type\":\"string\"}}}}}}}}",
        "lifecycle": {
          "create_before_destroy": true
        },
        "name": "api-c895068c"
      }
    },
    "aws_api_gateway_stage": {
      "cloudApi_api_stage_BBB283E4": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/api/stage",
            "uniqueId": "cloudApi_api_stage_BBB283E4"
          }
        },
        "deployment_id": "${aws_api_gateway_deployment.cloudApi_api_deployment_545514BF.id}",
        "rest_api_id": "${aws_api_gateway_rest_api.cloudApi_api_2B334D75.id}",
        "stage_name": "prod"
      }
    },
    "aws_cloudwatch_log_group": {
      "cloudApi_OnRequest0_CloudwatchLogGroup_3E53832E": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest0/CloudwatchLogGroup",
            "uniqueId": "cloudApi_OnRequest0_CloudwatchLogGroup_3E53832E"
          }
        },
        "name": "/aws/lambda/OnRequest0-c8dd1349",
        "retention_in_days": 30
      },
      "cloudApi_OnRequest1_CloudwatchLogGroup_167919D9": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest1/CloudwatchLogGroup",
            "uniqueId": "cloudApi_OnRequest1_CloudwatchLogGroup_167919D9"
          }
        },
        "name": "/aws/lambda/OnRequest1-c8a86267",
        "retention_in_days": 30
      }
    },
    "aws_iam_role": {
      "cloudApi_OnRequest0_IamRole_0E0166CB": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest0/IamRole",
            "uniqueId": "cloudApi_OnRequest0_IamRole_0E0166CB"
          }
        },
        "assume_role_policy": "{\"Version\":\"2012-10-17\",\"Statement\":[{\"Action\":\"sts:AssumeRole\",\"Principal\":{\"Service\":\"lambda.amazonaws.com\"},\"Effect\":\"Allow\"}]}"
      },
      "cloudApi_OnRequest1_IamRole_9911D256": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest1/IamRole",
            "uniqueId": "cloudApi_OnRequest1_IamRole_9911D256"
          }
        },
        "assume_role_policy": "{\"Version\":\"2012-10-17\",\"Statement\":[{\"Action\":\"sts:AssumeRole\",\"Principal\":{\"Service\":\"lambda.amazonaws.com\"},\"Effect\":\"Allow\"}]}"
      }
    },
    "aws_iam_role_policy": {
      "cloudApi_OnRequest0_IamRolePolicy_8DEF6CA2": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest0/IamRolePolicy",
            "uniqueId": "cloudApi_OnRequest0_IamRolePolicy_8DEF6CA2"
          }
        },
        "policy": "{\"Version\":\"2012-10-17\",\"Statement\":[{\"Action\":[\"s3:List*\",\"s3:GetObject*\",\"s3:GetBucket*\"],\"Resource\":[\"${aws_s3_bucket.A_cloudBucket_DFCC9367.arn}\",\"${aws_s3_bucket.A_cloudBucket_DFCC9367.arn}/*\"],\"Effect\":\"Allow\"}]}",
        "role": "${aws_iam_role.cloudApi_OnRequest0_IamRole_0E0166CB.name}"
      },
      "cloudApi_OnRequest1_IamRolePolicy_7A5A1217": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest1/IamRolePolicy",
            "uniqueId": "cloudApi_OnRequest1_IamRolePolicy_7A5A1217"
          }
        },
        "policy": "{\"Version\":\"2012-10-17\",\"Statement\":[{\"Effect\":\"Allow\",\"Action\":\"none:null\",\"Resource\":\"*\"}]}",
        "role": "${aws_iam_role.cloudApi_OnRequest1_IamRole_9911D256.name}"
      }
    },
    "aws_iam_role_policy_attachment": {
      "cloudApi_OnRequest0_IamRolePolicyAttachment_442E974F": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest0/IamRolePolicyAttachment",
            "uniqueId": "cloudApi_OnRequest0_IamRolePolicyAttachment_442E974F"
          }
        },
        "policy_arn": "arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole",
        "role": "${aws_iam_role.cloudApi_OnRequest0_IamRole_0E0166CB.name}"
      },
      "cloudApi_OnRequest1_IamRolePolicyAttachment_741E736E": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest1/IamRolePolicyAttachment",
            "uniqueId": "cloudApi_OnRequest1_IamRolePolicyAttachment_741E736E"
          }
        },
        "policy_arn": "arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole",
        "role": "${aws_iam_role.cloudApi_OnRequest1_IamRole_9911D256.name}"
      }
    },
    "aws_lambda_function": {
      "cloudApi_OnRequest0_E65A93DD": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest0/Default",
            "uniqueId": "cloudApi_OnRequest0_E65A93DD"
          }
        },
        "architectures": [
          "arm64"
        ],
        "environment": {
          "variables": {
            "BUCKET_NAME_5c35566c": "${aws_s3_bucket.A_cloudBucket_DFCC9367.bucket}",
            "NODE_OPTIONS": "--enable-source-maps",
            "WING_FUNCTION_NAME": "OnRequest0-c8dd1349",
            "WING_TARGET": "tf-aws"
          }
        },
        "function_name": "OnRequest0-c8dd1349",
        "handler": "index.handler",
        "memory_size": 1024,
        "publish": true,
        "role": "${aws_iam_role.cloudApi_OnRequest0_IamRole_0E0166CB.arn}",
        "runtime": "nodejs18.x",
        "s3_bucket": "${aws_s3_bucket.Code.bucket}",
        "s3_key": "${aws_s3_object.cloudApi_OnRequest0_S3Object_FDBBBF9D.key}",
        "timeout": 60,
        "vpc_config": {
          "security_group_ids": [],
          "subnet_ids": []
        }
      },
      "cloudApi_OnRequest1_3D65B7B4": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest1/Default",
            "uniqueId": "cloudApi_OnRequest1_3D65B7B4"
          }
        },
        "architectures": [
          "arm64"
        ],
        "environment": {
          "variables": {
            "BUCKET_NAME_5c35566c": "${aws_s3_bucket.A_cloudBucket_DFCC9367.bucket}",
            "NODE_OPTIONS": "--enable-source-maps",
            "WING_FUNCTION_NAME": "OnRequest1-c8a86267",
            "WING_TARGET": "tf-aws"
          }
        },
        "function_name": "OnRequest1-c8a86267",
        "handler": "index.handler",
        "memory_size": 1024,
        "publish": true,
        "role": "${aws_iam_role.cloudApi_OnRequest1_IamRole_9911D256.arn}",
        "runtime": "nodejs18.x",
        "s3_bucket": "${aws_s3_bucket.Code.bucket}",
        "s3_key": "${aws_s3_object.cloudApi_OnRequest1_S3Object_DB31ECF4.key}",
        "timeout": 60,
        "vpc_config": {
          "security_group_ids": [],
          "subnet_ids": []
        }
      }
    },
    "aws_lambda_permission": {
      "cloudApi_api_permission-GET-2d589ee9_3D8411D8": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/api/permission-GET-2d589ee9",
            "uniqueId": "cloudApi_api_permission-GET-2d589ee9_3D8411D8"
          }
        },
        "action": "lambda:InvokeFunction",
        "function_name": "${aws_lambda_function.cloudApi_OnRequest1_3D65B7B4.function_name}",
        "principal": "apigateway.amazonaws.com",
        "source_arn": "${aws_api_gateway_rest_api.cloudApi_api_2B334D75.execution_arn}/*/GET/bar",
        "statement_id": "AllowExecutionFromAPIGateway-GET-2d589ee9"
      },
      "cloudApi_api_permission-GET-4273ae49_974F3EC5": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/api/permission-GET-4273ae49",
            "uniqueId": "cloudApi_api_permission-GET-4273ae49_974F3EC5"
          }
        },
        "action": "lambda:InvokeFunction",
        "function_name": "${aws_lambda_function.cloudApi_OnRequest0_E65A93DD.function_name}",
        "principal": "apigateway.amazonaws.com",
        "source_arn": "${aws_api_gateway_rest_api.cloudApi_api_2B334D75.execution_arn}/*/GET/foo",
        "statement_id": "AllowExecutionFromAPIGateway-GET-4273ae49"
      }
    },
    "aws_s3_bucket": {
      "A_cloudBucket_DFCC9367": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/A/cloud.Bucket/Default",
            "uniqueId": "A_cloudBucket_DFCC9367"
          }
        },
        "bucket_prefix": "cloud-bucket-c8eec589-",
        "force_destroy": false
      },
      "Code": {
        "//": {
          "metadata": {
            "path": "root/Default/Code",
            "uniqueId": "Code"
          }
        },
        "bucket_prefix": "code-c84a50b1-"
      }
    },
    "aws_s3_object": {
      "cloudApi_OnRequest0_S3Object_FDBBBF9D": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest0/S3Object",
            "uniqueId": "cloudApi_OnRequest0_S3Object_FDBBBF9D"
          }
        },
        "bucket": "${aws_s3_bucket.Code.bucket}",
        "key": "<ASSET_KEY>",
        "source": "<ASSET_SOURCE>"
      },
      "cloudApi_OnRequest1_S3Object_DB31ECF4": {
        "//": {
          "metadata": {
            "path": "root/Default/Default/cloud.Api/OnRequest1/S3Object",
            "uniqueId": "cloudApi_OnRequest1_S3Object_DB31ECF4"
          }
        },
        "bucket": "${aws_s3_bucket.Code.bucket}",
        "key": "<ASSET_KEY>",
        "source": "<ASSET_SOURCE>"
      }
    }
  }
}
```
