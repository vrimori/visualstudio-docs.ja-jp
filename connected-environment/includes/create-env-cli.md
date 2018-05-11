---
ms.topic: include
ms.openlocfilehash: 97f9885780c9f697cfc6a58b78054761fdcd725d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
## <a name="create-a-kubernetes-development-environment-in-azure"></a>Azure で Kubernetes 開発環境を作成する
Connected Environment を使用すれば、Azure で完全に管理され、開発用に最適化された、Kubernetes ベースの環境を作成できます。 このコマンドによって、`eastus` に `mydevenvironment` という名前の環境が作成されます。
```cmd
vsce env create --name mydevenvironment --location eastus
```

サポートされる場所: `eastus`、`westeurope`

> [!Note]
> このコマンドには約 6 分かかります。 待たずにこのガイドを続行できます。
