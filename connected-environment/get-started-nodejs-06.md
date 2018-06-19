---
title: クラウドで Kubernetes を使用して、コンテナーを含む Node.js 開発環境を作成する - 手順 6 - チーム開発について学習する | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883580"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Connected Environment で Node.js の使用を開始する

前の手順: [別のコンテナーで実行されているサービスを呼び出す](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

実際の動作を見てみましょう。
1. `mywebapi` の VS Code ウィンドウに移動して、次のように既定の GET `/` ハンドラーのコードを編集します。

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [次へ](get-started-nodejs-07.md)

