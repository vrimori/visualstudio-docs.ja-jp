---
title: VS Shell 配置
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
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