---
title: "プロファイリングの新機能 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: f93c61e084378cd702ea8f190e1661c03bbc9c51
ms.lasthandoff: 03/08/2017

---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] プロファイリング ツールの新機能
診断ツールに、修正が必要なアプリの問題を識別できる新しい視覚化が追加されました。 診断ツールに ASP.NET アプリのサポートが追加されました。

詳細については、[[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] のリリース ノート](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag) をご覧ください。

パフォーマンス分析の主な領域に重点を置くことができる、**概要**タブがツールに追加されました。 概要タブには発生したイベントの数が表示され、ヒープのスナップショットを作成して、CPU 使用率のデータ収集を直ちに有効にすることができます。 このビューには、[Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) または [UI Analysis](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis) のイベントが表示されます。 また、Visual Studio Enterprise では、ビューに IntelliTrace イベントも表示されます。

![診断ツールの概要タブ](~/profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

CPU 使用率ツールに[新しい視覚化](../profiling/Beginners-Guide-to-Performance-Profiling.md)が加えられ、パフォーマンスの問題の原因になっている可能性が最も高い関数を識別できます。 新しい**呼び出し元/呼び出し先**ビューによって、選択した関数に対して、または選択した関数から行われる関数呼び出しのコストを調べることができます。

![診断ツールの [呼び出し元/呼び出し先] ビュー](~/profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>関連項目  
 [プロファイリング ツール](../profiling/profiling-tools.md)
