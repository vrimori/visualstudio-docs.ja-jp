---
title: "方法: ASP.NET Web アプリケーション用にコード分析を構成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: ASP.NET Web アプリケーション用にコード分析を構成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] および [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] では、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションに適用するコード分析*規則セット*を一覧から選択できます。  既定の規則セットは Microsoft 最小推奨規則です。  Web サイトに適用する別の規則セットを選択することもできます。  
  
### ASP.NET ページ フレームワーク プロジェクトの規則セットを構成するには  
  
1.  **ソリューション エクスプローラー**で Web サイトを選択します。  
  
2.  **\[分析\]** メニューの **\[Web サイトのコード分析を構成する\]** をクリックします。  
  
3.  ソリューションを選択し、そのソリューションに複数のプロジェクトが含まれている場合、**\[構成\]** ボックスの一覧と **\[プラットフォーム\]** ボックスの一覧からビルド構成とターゲット オペレーティング システムを選択します。  
  
4.  ソリューション内のプロジェクトごとに、**\[ルール セット\]** 列をクリックし、実行する規則セットの名前をクリックします。  
  
5.  既定では、コード分析はソリューション内のすべてのプロジェクトで実行されます。  特定のプロジェクトでコード分析を無効または有効にするには、次の手順を実行します。  
  
    1.  プロジェクト名を右クリックし、\[プロパティ\] をクリックします。  
  
    2.  **\[コード分析を有効にする\]** チェック ボックスをオンまたはオフにします。  **\[分析\]** メニューの **\[コード分析を Web サイトで実行\]** をクリックして、コード分析を手動で実行することもできます。  
  
6.  **\[この規則セットを実行\]** ドロップダウン リストで、次の手順を実行します。  
  
    -   使用する規則セットをクリックします。  
  
    -   セットの一覧にない、既存のカスタム規則を指定するに **\[\<参照\>\]** を選択します。  
  
    -   カスタム規則セットを定義します。  詳細については、「[カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)」を参照してください。