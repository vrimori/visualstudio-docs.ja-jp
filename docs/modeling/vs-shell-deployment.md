---
title: "VS Shell 配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# VS Shell 配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

分離シェルはVisual Studio の機能がドメイン固有言語とやり取りするために必要な方法とそのソリューションが表示されるかを判別することができます。  Visual Studio 分離シェルにする方法の詳細については[分離シェルをカスタマイズします。](../extensibility/customizing-the-isolated-shell.md) を参照してください。  [Customizing the Isolated Shell](http://msdn.microsoft.com/ja-jp/d75463cd-1155-42e4-8b7a-046ed6becbbf) の分離シェルをカスタマイズする方法に関する詳細な情報を確認できます。  
  
### Visual Studio シェルを配置先として設定するには  
  
1.  **DslPackage** のプロジェクトでは**source.extension.tt** を開きます。  
  
2.  `<SupportedProducts>` の対象 :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     分離シェル パッケージの名前に置き換えます *MyIsolatedShell*。