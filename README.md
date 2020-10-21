# lambda-s3

### 検証構成
S3 → Lambda

### デプロイ

* build  
  `./gradlew packageBig`でにzipファイルが作成されるのでLambdaに登録  


### helloworld

* Lambdaトリガ
  `s3://inspection-55/lambda-s3/input`へのPUTをトリガーとして設定

* 下記にtestファイルをPUT  
  ```
  s3://inspection-55/lambda-s3/input
  ```
  
* 出力結果  
  下記がCloudWatchLogsに出力される  
  ```
  2020-10-21 14:43:41 40ba6661-e4a5-4cca-a8e5-35b6f3587203 INFO  Handler - SOURCE BUCKET: inspection-55
  2020-10-21 14:43:41 40ba6661-e4a5-4cca-a8e5-35b6f3587203 INFO  Handler - SOURCE KEY: lambda-s3/input/test
  2020-10-21 14:43:41 40ba6661-e4a5-4cca-a8e5-35b6f3587203 INFO  Util - EVENT: {
    "records": [
      {
        "awsRegion": "ap-northeast-1",
        "eventName": "ObjectCreated:Put",
        "eventSource": "aws:s3",
        "eventTime": {
          "iMillis": 1603291419353,
          "iChronology": {
            "iBase": {
              "iMinDaysInFirstWeek": 4
            }
          }
        },
        "eventVersion": "2.1",
        "requestParameters": {
          "sourceIPAddress": "218.110.156.245"
        },
        "responseElements": {
          "xAmzId2": "AqCvm9FIqZWJe9+Bn9qbevnXxLZkZq24jtYSs0aHL3DBOTuIkVOro2vQDguc5AMgz2tOpfYwnaHWOlvUif+n2PuhVhQxAulz",
          "xAmzRequestId": "CZ6YFNDVEQ3GEP2Y"
        },
        "s3": {
          "configurationId": "603455b9-d321-4084-9c00-afd360adcf9c",
          "bucket": {
            "name": "inspection-55",
            "ownerIdentity": {
              "principalId": "A3V36KCH1X15WI"
            },
            "arn": "arn:aws:s3:::inspection-55"
          },
          "object": {
            "key": "lambda-s3/input/test",
            "size": 4,
            "eTag": "098f6bcd4621d373cade4e832627b4f6",
            "versionId": "",
            "sequencer": "005F90491BB0680095"
          },
          "s3SchemaVersion": "1.0"
        },
        "userIdentity": {
          "principalId": "AWS:AIDAWTE4H7GJP4CE2RDMB"
        }
      }
    ]
  }
  ```


### 参考情報

* チュートリアル  
  https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/with-s3.html

* プロジェクト  
  https://github.com/awsdocs/aws-lambda-developer-guide/tree/master/sample-apps/java-events-v1sdk
