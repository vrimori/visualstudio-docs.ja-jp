---
title: クラウドで Kubernetes を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 6 - チーム開発について学習する | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Connected Environment で .NET Core の使用を開始する

前の手順: [別のコンテナーを呼び出す](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

実際の動作を見てみましょう。
1. `mywebapi` の VS Code ウィンドウに移動して、次のように `string Get(int id)` メソッドのコードを編集します。

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [次へ](get-started-netcore-07.md)
