---
title: "方法: マネージ コード プロジェクトのコード分析を構成する | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "コード分析、選択 (ルール セットを)"
  - "コード分析、ルール セット"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: マネージ コード プロジェクトのコード分析を構成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、および [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] では、マネージ コード プロジェクトに適用するコード分析*規則セット*を一覧から選択できます。  既定の規則セットは Microsoft 最小推奨規則です。  ソリューション内の 1 つのプロジェクトまたはすべてのプロジェクトに別の規則セットを適用することもできます。  
  
> [!NOTE]
>  ASP.NET Web アプリケーションの規則セットの構成方法の詳細については、「[方法: ASP.NET Web アプリケーション用にコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)」を参照してください。  
  
### .NET Framework プロジェクトの規則セットを構成するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトをクリックします。  
  
2.  **\[分析\]** メニューの **\[*ProjectName* のコード分析を構成する\]** をクリックします。  
  
3.  **\[構成\]** および **\[プラットフォーム\]** の一覧で、ビルド構成とターゲット プラットフォームをクリックします。  
  
4.  選択した構成を使用してプロジェクトをビルドするたびにコード分析を実行するには、**\[ビルドに対するコード分析の有効化 \(CODE\_ANALYSIS 定数を定義\)\]** チェック ボックスをオンにします。  **\[分析\]** メニューの **\[*ProjectName*でコード分析を実行\]** をクリックして、コード分析を手動で実行することもできます。  
  
5.  既定では、外部ツールによって自動的に生成されたコードからの警告はコード分析では報告されません。  生成されたコードからの警告を表示するには、**\[生成されたコードから結果を表示しない\]** チェック ボックスをオフにします。  
  
    > [!NOTE]
    >  コード分析のエラーおよび警告がフォームやテンプレートで表示される場合、このオプションを使用しても、生成されたコードからこのエラーおよび警告の出力は抑制されません。  フォームまたはテンプレートのソース コードは表示することも保持することもできます。  
  
6.  **\[この規則セットを実行\]** ボックスの一覧で、次のいずれかの操作を行います。  
  
    -   使用する規則セットをクリックします。  
  
    -   **\[\<参照\>\]** をクリックして、一覧にない、既存のカスタム規則セットを指定します。  
  
    -   カスタム規則セットを定義します。  
  
         詳細については、「[カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)」を参照してください。  
  
## 参照  
 [チュートリアル: カスタム規則セットの構成と使用](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)