---
title: '方法: 有効にして、マネージ コードの完全ソリューション解析を無効にする |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: af0aae4020182f6414d44a2004f98a6fc0df23ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221872"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>方法: 有効にして、マネージ コードの完全ソリューション解析を無効にします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注]
>  このトピックでは、Visual Studio 2015 Update 3 RC にのみ以降に適用されます。  
  
 *完全ソリューション解析*は Visual Studio の機能で開いている Visual c# または Visual Basic ファイルのみ、ソリューションまたはオープンおよびクローズされた両方 Visual c# または Visual Basic ファイル、ソリューション内のコード分析の問題が発生するかどうかを選択することができます。  
  
 すべてのファイルですべての問題が発生することは役立ちますが、できます邪魔で Visual Studio をさらに低速なソリューションが非常に大きいまたは多数のファイルがある場合。  示されている問題の数を制限し、Visual Studio のパフォーマンスを向上させる、完全ソリューション解析を無効にすることができます。 場合は簡単に、この機能を再有効化することができます。  
  
#### <a name="to-toggle-full-solution-analysis"></a>完全ソリューション解析を切り替える  
  
1.  Visual Studio のメイン メニューで、次のように選択します。**ツール** &#124; **オプション**を表示する、**オプション** ダイアログ ボックス。  
  
2.  **オプション** ダイアログ ボックスで、選択**テキスト エディター** &#124; **c#** または**基本的な** &#124; **詳細**.  
  
3.  選択、**完全ソリューション解析を有効にする**チェック ボックスを完全なソリューション分析を有効または無効にするボックスをオフにします。 選択、 **OK**終わったときにボタンをクリックします。  
  
     ![完全なソリューション分析 チェック ボックスを有効にします。](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>結果を有効にして、完全ソリューション解析を無効にします。  
 次のスクリーン ショットでは、完全ソリューション解析を有効にすると、結果を確認できます。 すべてのエラーとコード分析の問題で*すべて*ソリューション内のファイルの表示、かどうか、開いているファイルかどうかに関係なく。  
  
 ![完全ソリューション解析を有効にします。](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 次のスクリーン ショットでは、完全ソリューション解析を無効にした後、同じソリューションから結果を示しています。 エラーとコード分析の問題のみは、エラー一覧にファイルが表示されるソリューションを開きます。  
  
 ![完全ソリューション解析を無効になっています。](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>完全ソリューション解析を自動的に無効化  
 Visual Studio を検出する場合は 200 MB またはシステム メモリの利用可能になりますが、自動的に無効になります完全ソリューション解析 (およびその他のいくつかの機能) が有効になっている場合。 このような場合は、通知するアラートが表示されます。 ボタンを使用するようにする場合に、完全なソリューション分析を再度有効にすることができます。  
  
 ![完全ソリューション解析を中断する警告テキスト](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>追加の詳細  
 完全ソリューション解析は既定では、Visual Basic を有効になっているし、無効になっている Visual c# 用。  
  
 Visual Studio Update 3 RC には、メモリ使用量が少なくなり、完全ソリューション解析が有効になっている場合でもアイドル、CPU 時間を減少が大幅に強化されたコード アナライザー診断 v2 エンジンが含まれています。



