---
title: VS Shell 配置
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 816997f971e90ddd27f8e24cdc1857559e04ff70
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="vs-shell-deployment"></a>VS Shell 配置

分離シェルでは、どの Visual Studio を判断できます。 機能、ドメイン固有言語、およびそのソリューションがどのように表示される必要がありますかと対話する必要があります。 Visual Studio 分離シェルの詳細については、次を参照してください。[分離シェルのカスタマイズ](../extensibility/customizing-the-isolated-shell.md)です。

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>配置ターゲットとして Visual Studio Shell を設定するには

1.  **DslPackage**プロジェクトを開き、 **source.extension.tt**です。

2.  `<SupportedProducts>`を挿入します。

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     置き換える*MyIsolatedShell*分離シェル パッケージの名前に置き換えます。