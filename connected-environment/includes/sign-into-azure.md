---
ms.topic: include
ms.openlocfilehash: 502bd8d206b43fc219c850ab870db35e6c3af1c0
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031211"
---
## <a name="sign-in-to-azure"></a>Azure にサインインする
開発環境を作成するには Azure にサインインする必要があります。 端末ウィンドウに次のコマンドを入力します。
```cmd
az login
```

> [!Note]
> Azure サブスクリプションをお持ちでなければ、[無料のアカウント](https://azure.microsoft.com/free)を作成できます。

### <a name="if-you-have-multiple-azure-subscriptions"></a>複数の Azure サブスクリプションをお持ちの場合...
次を実行すると、自分のサブスクリプションを表示できます。 
```cmd
az account list
```
JSON 出力に `isDefault: true` が表示されたサブスクリプションを見つけます。
これが使用するサブスクリプションではない場合、既定のサブスクリプションを変更できます。
```cmd
az account set --subscription <subscription ID>
```
