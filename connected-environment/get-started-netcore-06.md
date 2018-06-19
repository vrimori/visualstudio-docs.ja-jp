---
title: クラウドで Kubernetes を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 6 - チーム開発について学習する | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884344"
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
