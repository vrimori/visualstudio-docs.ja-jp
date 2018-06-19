---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
ms.locfileid: "32030819"
---
## <a name="clean-up"></a>クリーンアップ
Azure で Connected Environment を完全に、その中で実行されているすべてのサービスを含めて削除するには、`vsce env rm` コマンドを使用します。 この操作は元に戻せないことにご留意ください。

次のサンプルでは、アクティブな Azure サブスクリプションの Connected Environment が一覧表示され、リソース グループ 'myenv-rg' にある 'myenv' という名前の環境が削除されます。

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

