---
title: "方法: ASP.NET Web アプリケーションのコード分析を構成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 51ece959ad0c33c4676e81203cacc025d9ef2884
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>方法: ASP.NET Web アプリケーション用にコード分析を構成する
[!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]と[!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)]コード分析の一覧から選択できます*ルール セット*に適用する[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web アプリケーションです。 既定の規則セットは、Microsoft Mininimum 推奨規則です。 Web サイトに適用する別のルールを選択することができます。  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>ASP.NET ページ フレームワーク プロジェクトの規則セットを構成するには  
  
1.  Web サイトを選択して**ソリューション エクスプ ローラー**です。  
  
2.  **分析** メニューのをクリックして**Web サイトのコード分析を構成する**です。  
  
3.  ソリューションを選択し、このソリューションに複数のプロジェクトは場合からのビルドの構成とターゲットのオペレーティング システムを選択して、**構成**と**プラットフォーム**を一覧表示します。  
  
4.  ソリューション内の各プロジェクトをクリックして、**ルール セット**列、および実行するセットのルールの名前をクリックします。  
  
5.  既定では、ソリューション内のすべてのプロジェクトでコード分析を実行します。 特定のプロジェクトのコード分析を有効または無効に、これらの手順に従います。  
  
    1.  プロジェクト名を右クリックし、[プロパティ] をクリックします。  
  
    2.  オンまたはオフ、**コード分析の有効化**チェック ボックスをオンします。 手動では選択してもコード分析を実行することができます**Web サイトでコード分析を実行**から、**分析**メニュー。  
  
6.  **この規則セットを実行**ドロップダウン リストで、これらの手順に従います。  
  
    -   使用する規則セットを選択します。  
  
    -   選択**\<参照 >**既存のカスタム規則セットを指定ではありません、ボックスの一覧です。  
  
    -   カスタム規則セットを定義します。 詳細については、次を参照してください。[カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)です。