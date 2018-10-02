---
title: コード マップ アナライザーを使った潜在的な問題の検索 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b15a6d95e2a64aa09d57cb4fba02ab0369be5799
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534831"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>コード マップ アナライザーを使用して潜在的な問題を検索する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[検索潜在的な問題のコードを使用してマップ アナライザー](https://docs.microsoft.com/visualstudio/modeling/find-potential-problems-using-code-map-analyzers)します。  
  
コード マップに対してアナライザーを実行して、複雑すぎるコードや、改良が必要なコードを特定できます。 たとえば、アナライザーを使用して次のような作業を実行できます。  
  
|**次のものが含まれたコードを見つける**|**問題の領域を調べて次のことを確認する**|  
|-------------------------------|--------------------------------------------|  
|ループまたは循環の依存関係|これらを単純化できないか確認する。また、これらの循環をブレークできないか検討する。|  
|多すぎる依存関係|実行している関数が多すぎないか確認する。または、これらの領域を変更した場合の影響を判断する。 適切な形式のコード マップには最小限の数の依存関係が表示される。 コードの保守、変更、テスト、再利用を容易にするために、これらの領域をリファクタリングして依存関係をより明確に定義できないか検討する。または、同様の関数を実行するコードをマージできないか検討する。|  
|依存関係なし|依存関係が必要かどうか確認する。または、このコードを削除する必要があるかどうか確認する。|  
  
## <a name="analyze-code-maps"></a>コード マップの分析  
  
1.  マップのツールバーで **[レイアウト]**、 **[アナライザー]** の順に選び、実行するアナライザーを選びます。  
  
    |**アナライザー**|**次のようなノードを特定する**|  
    |------------------|--------------------------------|  
    |**循環参照アナライザー**|相互に循環する依存関係を持つノード。 **注:** 内にある循環依存関係、**ジェネリック**グループを展開するときに、グループは、マップに表示されません。|  
    |**ハブ検索アナライザー**|緊密に連結されたノードの上位 25 % にあるノード<br /><br /> **マップ上の他のすべてのノードを非表示にするには**<br /><br /> -マップのショートカット メニューを開き、選択**詳細**、**選択**、**以外を非表示**します。<br />     マップで選ばれていないノードが非表示にされ、アナライザーで新しいノードがハブとして識別されます。|  
    |**未参照ノード アナライザー**|他のノードからの参照がないノード。 **注意:** コードが使用されていないと仮定する前にこのような場合のそれぞれについて確認します。 XAML の依存関係や実行時の依存関係などの特定の依存関係は、コード内で静的には見つかりません。|  
  
 コード マップのアナライザーは、適用後も引き続き実行されます。 マップを変更すると、適用されたアナライザーが、更新されたマップを自動的に再処理します。 アナライザーの実行を停止するには、マップのツールバーで、 **[レイアウト]**、 **[アナライザー]** の順に選びます。 選んだアナライザーをオフにします。  
  
> [!TIP]
>  サイズの非常に大きなマップが存在する場合、アナライザーを実行するとメモリ不足例外が発生する可能性があります。 例外が発生した場合は、マップを編集してスコープを縮小するか、より小さいマップを生成してから、アナライザーを実行します。  
  
## <a name="see-also"></a>関連項目  
 [ソリューション間の依存関係をマップします。](../modeling/map-dependencies-across-your-solutions.md)   
 [アプリケーションをデバッグするコード マップの使用](../modeling/use-code-maps-to-debug-your-applications.md)   
 [デバッグ中の、呼び出し履歴に関するメソッドのマッピング](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)



