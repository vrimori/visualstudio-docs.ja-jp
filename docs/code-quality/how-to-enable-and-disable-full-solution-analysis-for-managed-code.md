---
title: "方法: を有効にして、マネージ コードの完全なソリューション分析を無効にする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 94cda949a713a773e5586e5b1ef284c6ba54839c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>方法: を有効にして、マネージ コードの完全なソリューション分析を無効にします。
> [!NOTE]
>  このトピックには、Visual Studio 2015 Update 3 RC にのみ以降が適用されます。  
  
 *完全ソリューション解析*Visual Studio の機能で開いている Visual c# または Visual Basic ファイル、ソリューションまたはソリューションのオープンとクローズの両方 Visual c# または Visual Basic ファイルでのみコード分析の問題が発生するかどうかを選択することができます。  
  
 すべてのファイル内のすべての問題を確認できるものは役立ちますが、なることが無駄なと Visual Studio も低下ソリューションが非常に大きいか、多くのファイルです。  表示の問題の数を制限して、Visual Studio のパフォーマンスを向上させる、完全なソリューション分析を無効にできます。 場合は簡単に、この機能を再有効化することができます。  
  
#### <a name="to-toggle-full-solution-analysis"></a>完全なソリューション分析を切り替える  
  
1.  Visual Studio で、メイン メニュー選択**ツール**&#124;です。**オプション**を表示する、**オプション** ダイアログ ボックス。  
  
2.  **オプション** ダイアログ ボックスで、選択**テキスト エディター** &#124;です。**C#**または**基本**&#124;です。**高度な**します。  
  
3.  選択、**完全ソリューション解析を有効にする**完全なソリューション分析を有効または無効にするボックスをオフにする チェック ボックスです。 選択、 **OK**終わったときにボタンをクリックします。  
  
     ![完全なソリューション分析 チェック ボックスを有効にします。] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>結果を有効にして、完全なソリューション分析を無効にします。  
 次のスクリーン ショットでは、完全なソリューション分析を有効にすると、結果を確認できます。 すべてのエラーとコード分析の問題で*すべて*ソリューション内のファイルの表示、かどうか、ファイルが開いているかに関係なく。  
  
 ![完全ソリューション解析を有効にします。] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 次のスクリーン ショットは、完全なソリューション分析を無効にした後、同じソリューションからの結果を示します。 エラーとでコード分析の問題だけは、エラー一覧にファイルが表示されるソリューションを開きます。  
  
 ![完全ソリューション解析を無効になっています。] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>完全なソリューション分析を自動的に無効化  
 Visual Studio では、ことが検出された場合 200 MB に使用できるシステム メモリの少ないが、自動的に無効に完全なソリューション分析 (およびその他の機能) が有効な場合またはします。 この場合、これを通知するアラートが表示されます。 ボタンを使用するようにする場合に、完全なソリューション分析を再度有効にすることができます。  
  
 ![完全ソリューション解析を中断する警告テキスト](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>追加の詳細  
 既定では、完全なソリューション分析は、Visual Basic および無効になっている Visual c# 可能です。  
  
 Visual Studio Update 3 RC には、メモリ使用量が少なくなり、完全なソリューション分析が有効になっている場合でも、アイドル状態に CPU 時間を減少が大幅に拡張されたコード アナライザー診断 v2 エンジンが含まれています。