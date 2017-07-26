---
title: "応答ファイルで Visual Studio インストールを自動化する | Microsoft Docs"
description: "{{プレースホルダー}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: c77f0321e50a27635e083d656cf6ba8011a4ef4d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/11/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>応答ファイルの設定を定義する方法
管理者は Visual Studio を展開するとき、`--in` パラメーターを利用して応答ファイルを指定できます。たとえば、次のようになります。

```
vs_enterprise.exe --in customInstall.json
```

応答ファイルは、その内容がコマンド ライン引数を反映する [JSON](http://json-schema.org/) ファイルです。  一般的に、コマンド ライン パラメーターが引数を取らない場合 (`--quiet` や `--passive` など)、応答ファイルの値は true/false にしてください。  引数を取る場合 (`--installPath <dir>` など)、応答ファイルの値は文字列にしてください。  引数を取り、コマンド ラインに何回も出てくる場合 (`--add <id>` など)、文字列の配列にしてください。

コマンド ラインに指定されているパラメーターは、応答ファイルの設定より優先されます。ただし、パラメーターが複数の入力値を取り (`--add` など)、コマンド ラインに入力された値が応答ファイルの設定と結合される場合を除きます。

# <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio の既定構成を設定する

`--layout` でネットワーク レイアウト キャッシュを作成した場合、最初の `response.json` ファイルがレイアウトで作成されます。

レイアウトを作成する管理者はレイアウトの `response.json` ファイルを変更することで、ユーザーがレイアウトから Visual Studio をインストールするときに表示される既定の設定を制御できます。  たとえば、管理者が特定のワークロードとコンポーネントを既定でインストールする場合、それらを追加するように `response.json` ファイルを構成できます。

Visual Studio セットアップをレイアウト フォルダーから実行すると、レイアウト フォルダーの応答ファイルが_自動的に_使用されます。  `--in` オプションの使用は必須ではありません。

オフライン レイアウト フォルダーで作成された `response.json` ファイルを更新することで、このレイアウトからインストールするユーザーの既定設定を定義できます。 **ただし、レイアウトが作成されたときに定義された既存プロパティをそのままにすることが重要です。**

レイアウトの基本 `response.json` ファイルはこれと似ていますが、値はインストールする製品またはチャネルのものになります。

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>レイアウト応答ファイルの内容の例
この例では、Visual Studio Enterprise、6 つの共通ワークロード、コンポーネントがインストールされます。UI 言語として英語とフランス語の両方がインストールされます。 これをテンプレートとして利用できます。ワークロードとコンポーネントを自分がインストールするものに変更してください。

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```
## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のワークロード ID とコンポーネント ID](workload-and-component-ids.md)

