---
title: '方法: ASP.NET Web アプリケーションのコード分析の構成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf7450341dd166977d67639f4f3762fae6ef89c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283908"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>方法: ASP.NET Web アプリケーション用にコード分析を構成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]と[!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]コード分析の一覧から選択できる*ルール セット*に適用する[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Web アプリケーション。 既定の規則セットは、Microsoft Mininimum 推奨規則です。 Web サイトに適用する別のルールを選択できます。  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>ASP.NET ページ フレームワーク プロジェクトの規則セットを構成するには  
  
1.  Web サイトを選択します。**ソリューション エクスプ ローラー**します。  
  
2.  **分析** メニューのをクリックして**Web サイトのコード分析を構成する**します。  
  
3.  ソリューションを選択し、ソリューションが 1 つ以上のプロジェクト場合、からビルド構成とターゲットのオペレーティング システムを選択、**構成**と**プラットフォーム**を一覧表示します。  
  
4.  ソリューション内の各プロジェクトをクリックして、**ルール セットの**列、および実行するルールの名前を設定 をクリックします。  
  
5.  既定では、ソリューション内のすべてのプロジェクトでコード分析を実行します。 無効にするか、または特定のプロジェクトのコード分析を有効にして、これらの手順に従います。  
  
    1.  プロジェクト名を右クリックし、[プロパティ] をクリックします。  
  
    2.  オンまたはオフ、**コード分析の有効化**チェック ボックスをオンします。 手動では選択してもコード分析を実行することができます**Web サイトでコード分析を実行**から、**分析**メニュー。  
  
6.  **この規則セットを実行**ドロップダウン リストで、これらの手順に従います。  
  
    -   使用する規則セットを選択します。  
  
    -   選択**\<参照 >** を既存のカスタム規則セットを指定されていないリスト。  
  
    -   カスタム規則セットを定義します。 詳細については、次を参照してください。[カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)です。



