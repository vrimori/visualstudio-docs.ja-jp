---
title: トラブルシューティング | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 0f35e31e3f3a109e65565592b56b6dc4177dd7c0
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="troubleshooting-guide"></a>トラブルシューティング ガイド

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>エラー 'アップストリーム接続エラーまたはヘッダーの前の切断/リセット'
サービスにアクセスしようとしているときに、このエラーが表示される可能性があります。 たとえば、ブラウザーでサービスの URL に移動する場合です。 

**理由:** コンテナー ポートが使用できません。 最も一般的な理由を以下に示します。 
* コンテナーがまだビルドおよび展開中です。 `vsce up` を実行するか、デバッガーを起動する場合に、コンテナーが正常に展開される前にそのコンテナーにアクセスしようとするとこのようになる場合があります。
* ポートの構成が、Dockerfile、Helm チャート、およびポートを開くすべてのサーバー コードの間で一致していません。

**次の操作を試してください。**
1. コンテナーがビルドおよび展開中である場合は、2、3 秒待ってからサーバーにもう一度アクセスしてみます。 
1. ポートの構成を確認します。 指定したポート番号は、以下のすべてのアセットで**同一**である必要があります。
    * **Dockerfile:** `EXPOSE` 命令で指定されます。
    * **[Helm チャート](https://docs.helm.sh):** サービスの `externalPort` と `internalPort` の値で指定されます (多くの場合、`values.yml` ファイルにあります)。
    * アプリケーション コードで開かれているすべてのポート (Node.js の場合): `var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>構成ファイルが見つかりません
`vsce up` を実行すると、`Config file not found: .../vsce.yaml` というエラーが表示されます。

**理由:** `vsce up` は、実行するコードのルート ディレクトリから実行する必要があります。コード フォルダーは、Connected Environment で実行するために初期化されている必要があります。

**次の操作を試してください。**
1. 現在のディレクトリをサービス コードを含むルート フォルダーに変更します。 
1. コード フォルダーに vsce.yaml ファイルがない場合は、`vsce init` を実行して Docker、Kubernetes、VSCE のアセットを生成します。

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>エラー: 'パイプ プログラム 'vsce' がコード 126 で予期せず終了しました。'
VS Code デバッガーを開始すると、このエラーが発生する場合があります。 これはバグです。

**次の操作を試してください。**
1. VS Code を閉じてからもう一度開きます。
2. もう一度 F5 を押します。


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>デバッグ エラー '構成されたデバッグの種類 'coreclr' はサポートされていません'
VS Code デバッガーを実行すると、`Configured debug type 'coreclr' is not supported.` というエラーが報告されます。

**理由:** 開発用コンピューターに Connected Environment の VS Code 拡張機能がインストールされていません。

**次の操作を試してください。**[Connected Environment の VS Code 拡張機能](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code)をインストールします。


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>Azure Portal に Connected Environment インスタンスが表示されません

**理由:** プレビューでは、Connected Environment の Azure Portal エクスペリエンスはまだ準備できていません。


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>型または名前空間の名前 'MyLibrary' が見つかりませんでした

**理由:** ビルド コンテキストは、既定ではプロジェクト/サービス レベルであるため、使用するライブラリ プロジェクトは見つかりません。

**次の操作を試してください。**実行する必要がある操作は次のとおりです。
1. vsce.yaml ファイルを変更して、ビルド コンテキストをソリューション レベルに設定します。
2. Dockerfile および Dockerfile.develop ファイルを変更して、新しいビルド コンテキストを基準に正しく csproj ファイルを参照するようにします。
3. .sln ファイルの横に .dockerignore ファイルを配置して、必要に応じて変更します。

https://github.com/sgreenmsft/buildcontextsample で例を見つけることができます。

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>環境作成時の 'Microsoft.ConnectedEnvironment/register/action' 承認エラー
環境を管理する際に、所有者または共同作成者のアクセス権がない Azure サブスクリプションで作業を行っている場合、次のエラーが表示されることがあります。
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**理由:** 選択した Azure サブスクリプションで Microsoft.ConnectedEnvironment 名前空間が登録されていません。

**次の操作を試してください。**所有者または共同作成者のアクセス権を持つユーザーは、以下の Azure CLI コマンドを実行して、Microsoft.ConnectedEnvironment 名前空間を手動で登録できます。

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>VSCE が既存の Dockerfile を使用してコンテナーをビルドしていないように見える 

**理由:** VSCE を、プロジェクト内の特定の Dockerfile をポイントするように構成することができます。 VSCE が予期した Dockerfile を使用してコンテナーをビルドしていないように見える場合は、VSCE にその場所を明示的に指示する必要がある場合があります。 

**次の操作を試してください。**プロジェクト内の VSCE で生成された `vsce.yaml` ファイルを開きます。 `configurations->develop->build->dockerfile` ディレクティブを使って、使用する Dockerfile をポイントします。

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```