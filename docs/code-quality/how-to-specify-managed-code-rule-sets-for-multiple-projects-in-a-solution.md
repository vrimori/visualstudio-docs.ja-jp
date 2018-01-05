---
title: "方法: ソリューション内の複数のプロジェクトに対してマネージ コード規則セットを指定して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 346ddadef815f4926b0a87a924a502ab2184de3e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>方法: ソリューション内の複数のプロジェクトに対してマネージ コード規則セットを指定する
既定では、ソリューションのすべてのマネージ プロジェクトには Microsoft 最小推奨規則コード分析を割り当てられた*ルール セット*です。 ソリューションのプロパティ ダイアログ ボックスで、ソリューションのプロジェクトに割り当てられる規則セットを変更できます。  
  
> [!NOTE]
>  既定では、プロジェクトのコード分析はビルド ステップとして実行されません。 ビルド ステップとしてコード分析を有効にするを参照してください。[する方法: マネージ コード プロジェクトのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)です。  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>マネージ コード ソリューション内の複数のプロジェクトに対して規則セットを指定するには  
  
1.  [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、または [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] で、ソリューションを開きます。  
  
2.  **分析** メニューのをクリックして**ソリューションのコード分析を構成する**です。  
  
3.  必要に応じて、展開**共通プロパティ**、クリックして**コード分析設定**です。  
  
4.  1 つ以上のプロジェクトに対して規則セットを指定できます。  
  
    -   個々のプロジェクトに対して規則セットを指定するには、プロジェクト名をクリックします。  
  
    -   複数のプロジェクトに対して規則セットを指定するには、Ctrl キーを押しながらプロジェクト名をクリックします。  
  
    -   ソリューションに含まれるすべてのプロジェクトを指定するには、Shift キーを押しながらプロジェクトの一覧内をクリックします。  
  
5.  クリックして、**ルール セット**フィールドのプロジェクトとセットを適用するルールの名前をクリックします。