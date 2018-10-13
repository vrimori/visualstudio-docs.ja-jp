---
title: '方法: マネージ コード プロジェクトのコード分析の構成 |Microsoft Docs'
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
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98f3d14b73b0219d0fcec4312648bf613f37378e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239188"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>方法: マネージド コード プロジェクトのコード分析を構成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]と[!INCLUDE[vsPro](../includes/vspro-md.md)]、コード分析の一覧から選択できる*ルール セット*マネージ コード プロジェクトに適用します。 既定の規則セットは Microsoft 最小推奨規則です。 ソリューション内の 1 つのプロジェクトまたはすべてのプロジェクトに別の規則セットを適用することもできます。  
  
> [!NOTE]
>  ASP.NET Web アプリケーションのルール セットを構成する方法については、次を参照してください。[方法: ASP.NET Web アプリケーションのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)します。  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework プロジェクトの規則セットを構成するには  
  
1.  **ソリューション エクスプ ローラー**プロジェクトをクリックします。  
  
2.  **分析** メニューのをクリックして**コード分析を構成** *ProjectName*します。  
  
3.  **構成**と**プラットフォーム**リスト、ビルド構成とターゲット プラットフォームをクリックします。  
  
4.  選択した構成を使用して、プロジェクトをビルドするたびに、コード分析を実行するには、選択、**を有効にするビルドに対するコード分析 (CODE_ANALYSIS 定数を定義します)** チェック ボックスをオンします。 手動では開くことでもコード分析を実行することができます、**分析**メニューをクリックすると**でコード分析を実行** *ProjectName*します。  
  
5.  既定では、外部ツールによって自動的に生成されたコードからの警告はコード分析では報告されません。 生成されたコードからの警告を表示するには、オフ、**結果生成されたコードを表示しない**チェック ボックスをオンします。  
  
    > [!NOTE]
    >  コード分析のエラーおよび警告がフォームやテンプレートで表示される場合、このオプションを使用しても、生成されたコードからこのエラーおよび警告の出力は抑制されません。 フォームまたはテンプレートのソース コードは表示することも保持することもできます。  
  
6.  **この規則セットを実行**ボックスの一覧で、次のいずれかの操作を行います。  
  
    -   使用する規則セットをクリックします。  
  
    -   クリックして **\<[参照...] >** を既存のカスタム規則セットを指定されていないリスト。  
  
    -   カスタム規則セットを定義します。  
  
         詳細については、次を参照してください。[カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: カスタム規則セットの構成と使用](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)



