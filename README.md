# infra

1. `tfstate ファイル` の保管先準備＆設定

    以下のファイルにある設定（S3バケット名、キー名）を見直し。
    必要に応じて AWS 上に対応する S3バケット を準備。

    `/10_infra/main.tf`

        ... 省略 ...

          backend "s3" {
            bucket  = "{バケット名}"
            key     = "{キー名}"
            region  = "ap-northeast-1"
            profile = "terraform"
          }
        }

        ... 省略 ...


1. `terraform.tfvars` ファイルの準備

    以下のファイルを作成。
    プロジェクト名、環境名、ユーザー名、パスワードはそれぞれ任意の値を設定。

    `/10_infra/terraform.tfvars`

        project     = "{プロジェクト名}"
        environment = "{環境名}"
        username    = "{管理ユーザー名}"
        password    = "{管理パスワード}"

    (*) 管理ユーザー名、管理パスワードは DB のアクセスで利用

# Required secrets

|Name|Value|
|---|---|
| `SLACK_WEBHOOK_URL` | Slack Incomming Webhook URL |
| `AWS_IAM_ROLE_ARN`  | AWS IAM Role ARN |

