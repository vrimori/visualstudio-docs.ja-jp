---
title: VS Shell 展開 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4964ce162efac640ea7581b4d3f26f3d50087319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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