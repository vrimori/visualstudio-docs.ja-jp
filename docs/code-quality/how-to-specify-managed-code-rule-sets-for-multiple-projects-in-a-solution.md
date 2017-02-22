---
title: "方法: ソリューション内の複数のプロジェクトに対してマネージ コード規則セットを指定する | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: ソリューション内の複数のプロジェクトに対してマネージ コード規則セットを指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定では、ソリューション内のすべてのマネージ プロジェクトに "Microsoft 最小推奨規則" コード分析*規則セット*が割り当てられます。  ソリューションのプロパティ ダイアログ ボックスで、ソリューションのプロジェクトに割り当てられる規則セットを変更できます。  
  
> [!NOTE]
>  既定では、プロジェクトのコード分析はビルド ステップとして実行されません。  コード分析をビルド ステップとして有効にする方法については、「[方法: マネージ コード プロジェクトのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)」を参照してください。  
  
### マネージ コード ソリューション内の複数のプロジェクトに対して規則セットを指定するには  
  
1.  [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、  [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、または [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] で、ソリューションを開きます。  
  
2.  **\[分析\]** メニューの **\[ソリューションのコード分析を構成する\]** をクリックします。  
  
3.  必要に応じて、**\[共通プロパティ\]** を展開し、**\[コード分析設定\]** をクリックします。  
  
4.  1 つ以上のプロジェクトに対して規則セットを指定できます。  
  
    -   個々のプロジェクトに対して規則セットを指定するには、プロジェクト名をクリックします。  
  
    -   複数のプロジェクトに対して規則セットを指定するには、Ctrl キーを押しながらプロジェクト名をクリックします。  
  
    -   ソリューションに含まれるすべてのプロジェクトを指定するには、Shift キーを押しながらプロジェクトの一覧内をクリックします。  
  
5.  プロジェクトの **\[ルール セット\]** フィールドをクリックし、適用する規則セットの名前をクリックします。