---
title: '方法: ソリューション内の複数のプロジェクトに対してマネージ コード規則セットの指定 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 42b04eb88e6edee2d8250ac29a26f4cfe6562a29
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539612"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>方法: ソリューション内の複数のプロジェクトに対してマネージド コード規則セットを指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ソリューション内の複数のプロジェクトにコード規則セットを管理されている指定](https://docs.microsoft.com/visualstudio/code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution)します。  
  
既定で、Microsoft 最小推奨規則のコード分析がこのソリューションのすべてのマネージ プロジェクトに割り当てられている*ルール セット*します。 ソリューションのプロパティ ダイアログ ボックスで、ソリューションのプロジェクトに割り当てられる規則セットを変更できます。  
  
> [!NOTE]
>  既定では、プロジェクトのコード分析はビルド ステップとして実行されません。 ビルドのステップとして、コード分析を有効にするのを参照してください。[方法: マネージ コード プロジェクトのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)します。  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>マネージド コード ソリューション内の複数のプロジェクトに対して規則セットを指定するには  
  
1.  [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、または [!INCLUDE[vsPro](../includes/vspro-md.md)] で、ソリューションを開きます。  
  
2.  **分析** メニューのをクリックして**ソリューションのコード分析を構成する**します。  
  
3.  必要に応じて、展開**共通プロパティ**、 をクリックし、**コード分析設定**します。  
  
4.  1 つ以上のプロジェクトに対して規則セットを指定できます。  
  
    -   個々のプロジェクトに対して規則セットを指定するには、プロジェクト名をクリックします。  
  
    -   複数のプロジェクトに対して規則セットを指定するには、Ctrl キーを押しながらプロジェクト名をクリックします。  
  
    -   ソリューションに含まれるすべてのプロジェクトを指定するには、Shift キーを押しながらプロジェクトの一覧内をクリックします。  
  
5.  をクリックして、**ルール セットの**フィールドのプロジェクトと、規則の名前の設定を適用する をクリックします。



