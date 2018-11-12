---
title: Publish-webapplicationvm |Microsoft Docs
description: 仮想マシンに web アプリケーションをデプロイする方法について説明します。 このスクリプトでは、存在していない場合に、Azure サブスクリプションに必要なリソースを作成します。
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003002"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (Windows PowerShell スクリプト)
仮想マシンへの web アプリケーションをデプロイします。 スクリプトが存在しない場合に、Azure サブスクリプションで、必要なリソースを作成します。

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>構成
展開の詳細を記述する JSON 構成ファイルへのパス。

| Aliases | none |
| --- | --- |
| 必須? |true |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

### <a name="subscriptionname"></a>SubscriptionName
仮想マシンを作成する Azure サブスクリプションの名前。

| Aliases | none |
| --- | --- |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |サブスクリプション ファイルでは、最初のサブスクリプション |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

### <a name="webdeploypackage"></a>WebDeployPackage
仮想マシンに発行する web デプロイ パッケージへのパス。 このパッケージを作成するには、Visual Studio で Web の発行ウィザードを使用します。 参照してください[方法: Visual Studio で Web 配置パッケージを作成する](https://msdn.microsoft.com/library/dd465323.aspx)します。

| Aliases | none |
| --- | --- |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

### <a name="allowuntrusted"></a>AllowUntrusted
True の場合は、信頼されたルート機関によって署名されていない証明書の使用を許可します。

| Aliases | none |
| --- | --- |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |False |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

### <a name="vmpassword"></a>VMPassword
仮想マシン アカウントの資格情報。 例:-vmpassword @{Name ="admin";パスワード ="password"}

| Aliases | none |
| --- | --- |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Azure SQL database の資格情報。 例:-databaseserverpassword @{Name ="admin";パスワード ="password"}

| Aliases | none |
| --- | --- |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
True の場合、印刷がスクリプトから出力ストリームにメッセージします。

| Aliases | none |
| --- | --- |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |False |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

## <a name="remarks"></a>Remarks
詳細については、スクリプトを使用して作成する方法の開発およびテスト環境を参照してください[開発環境およびテスト環境に発行する Windows PowerShell スクリプトを使用した](vs-azure-tools-publishing-using-powershell-scripts.md)します。

JSON 構成ファイルには、展開する新機能の詳細を指定します。 これには、名前、アフィニティ グループ、VHD イメージ、および仮想マシンのサイズなど、プロジェクトの作成時に指定した情報が含まれます。 また、存在する場合、仮想マシンをプロビジョニングするデータベースのエンドポイントが含まれていて、web デプロイメント パラメーター。 次のコードは、JSON 構成ファイルの例を示しています。

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

プロビジョニングされる内容を変更する JSON 構成ファイルを編集することができます。 仮想マシンとクラウド サービスが必要ですが、データベースのセクションは省略可能です。

