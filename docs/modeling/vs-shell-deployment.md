---
title: "VS Shell 展開 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 26b5075c36b152ecc44d65428521e191e6053609
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
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