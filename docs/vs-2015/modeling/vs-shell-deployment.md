---
title: VS Shell 配置 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e1a1bd92d1a0b91aa01d940695cd780f7e63c098
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548156"
---
# <a name="vs-shell-deployment"></a>VS Shell 配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[VS Shell 配置](https://docs.microsoft.com/visualstudio/modeling/vs-shell-deployment)します。  
  
分離のシェルでは、Visual Studio を確認できます。 機能、ドメイン固有言語およびそのソリューションを表示する方法と対話する必要があります。 Visual Studio 分離シェルの詳細については、次を参照してください。[分離シェルのカスタマイズ](../extensibility/customizing-the-isolated-shell.md)します。 分離シェルをカスタマイズする方法の詳細を検索する[分離シェルのカスタマイズ](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf)します。  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>配置ターゲットとして Visual Studio Shell を設定するには  
  
1.  **DslPackage**プロジェクトを開き、 **source.extension.tt**します。  
  
2.  `<SupportedProducts>`を挿入します。  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     置換*MyIsolatedShell*分離シェルのパッケージの名前に置き換えます。



