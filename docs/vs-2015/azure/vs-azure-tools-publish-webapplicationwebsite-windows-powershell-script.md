---
title: Publish-webapplicationwebsite (Windows PowerShell スクリプト) |Microsoft Docs
description: Azure の web サイトに web プロジェクトを発行する方法について説明します。 このスクリプトでは、存在していない場合に、Azure サブスクリプションに必要なリソースを作成します。
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 175181d5d866e9d7fab51eaf7c3262e47d0ed6a8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002892"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell スクリプト)
## <a name="syntax"></a>構文
Azure の web サイトに web プロジェクトを発行します。 スクリプトが存在しない場合に、Azure サブスクリプションで、必要なリソースを作成します。

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>構成
展開の詳細を記述する JSON 構成ファイルへのパス。

| パラメーター | 既定値 |
| --- | --- |
| Aliases |none |
| 必須? |true |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

## <a name="subscriptionname"></a>SubscriptionName
Web サイトを作成する Azure サブスクリプションの名前。

| パラメーター | 既定値 |
| --- | --- |
| Aliases |none |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

## <a name="webdeploypackage"></a>WebDeployPackage
Web サイトに発行する web デプロイ パッケージへのパス。 このパッケージを作成するには、Visual Studio で Web の発行ウィザードを使用します。 詳細については、次を参照してください。 [Azure Cloud Services と ASP.NET の概要](http://go.microsoft.com/fwlink/p/?LinkID=623089)します。

| パラメーター | 既定値 |
| --- | --- |
| Aliases |none |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
ユーザー名とパスワードを azure SQL database。

| パラメーター | 既定値 |
| --- | --- |
| Aliases |none |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |none |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
True の場合、印刷がスクリプトから出力ストリームにメッセージします。

| パラメーター | 既定値 |
| --- | --- |
| Aliases |none |
| 必須? |False |
| 位置 |名前付き |
| 既定値 |False |
| パイプラインの入力をそのまま使用しますか。 |False |
| ワイルドカード文字を使用しますか。 |False |

## <a name="remarks"></a>Remarks
詳細については、スクリプトを使用して作成する方法の開発およびテスト環境を参照してください[開発環境およびテスト環境に発行する Windows PowerShell スクリプトを使用した](vs-azure-tools-publishing-using-powershell-scripts.md)します。

JSON 構成ファイルには、展開する新機能の詳細を指定します。 これには、web サイトのユーザー名と名前など、プロジェクトの作成時に指定する情報が含まれます。 存在する場合、プロビジョニングを行うデータベースもあります。 次のコードは、JSON 構成ファイルの例を示しています。

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "West US"
            },
            "databases": [
                {
                    "connectionStringName": "DefaultConnection",
                    "databaseName": "WebApplication10554_db",
                    "serverName": "iss00brc88",
                    "user": "sqluser2",
                    "password": "",
                    "edition": "",
                    "size": "",
                    "collation": "",
                    "location": "West US"
                }
            ]
        }
    }

展開されているものを変更する JSON 構成ファイルを編集することができます。 Web サイトのセクションが必要ですが、データベース セクションは省略可能です。

## <a name="next-steps"></a>次の手順
詳細については、次を参照してください[Publish-webapplicationvm (Windows PowerShell スクリプト)。](vs-azure-tools-publish-webapplicationvm.md)

