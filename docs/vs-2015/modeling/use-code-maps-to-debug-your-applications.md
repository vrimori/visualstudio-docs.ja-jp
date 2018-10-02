---
title: コード マップを使用してアプリケーションをデバッグする |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 51
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: f3dd19804a8e7749a976b5334ea691918eeae906
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539371"
---
# <a name="use-code-maps-to-debug-your-applications"></a>コード マップを使用してアプリケーションをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コード マップをアプリケーションのデバッグ](https://docs.microsoft.com/visualstudio/modeling/use-code-maps-to-debug-your-applications)します。  
  
コード マップを使用すると、大規模なコード ベース、よく知らないコード、またはレガシ コードでの見失いを回避できます。 たとえば、デバッグの際は、多数のファイルとプロジェクトにわたってコードに注意を払うことが必要になる場合があります。 コード マップを使用すると、これらのコード内を移動して、コード間の関係を確認できます。 これにより、このコードを頭の中で追跡したり、別の図を描画したりする必要はありません。 コード マップがあれば、作業を中断しても作業中のコードを思い出すのに役立ちます。  
  
 ![コード マップ&#45;コード内の関係をマップ](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **エディターでカーソルが表示されます。、緑色の矢印が表示されます。**  
  
 コマンドとコード マップを使用する場合に使用できる操作の詳細については、次を参照してください。[参照およびコード マップの再配置](../modeling/browse-and-rearrange-code-maps.md)します。  
  
## <a name="understand-the-problem"></a>問題を把握する  
 作業中の描画プログラムにバグがあるとします。 バグを再現するには、Visual Studio およびキーを押して、ソリューションを開いた**F5**デバッグを開始します。  
  
 線を描画し、選択したときに**最後のストロークを元に戻す**、次の行を描画するまで何も起こりません。  
  
 ![コード マップ&#45;バグの再現コード](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 したがって、`Undo` メソッドを検索して調査を開始します。 `PaintCanvas` クラスでこれが見つかります。  
  
 ![コード マップ&#45;コード](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## <a name="start-mapping-the-code"></a>コードのマップを開始する  
 ここで、`undo` メソッドとその関係のマップを開始します。 コード エディターで、`undo` メソッドとその参照するフィールドを、新しいコード マップに追加します。 新しいマップを作成するときは、コードにインデックスを付けるのに時間がかかる場合があります。 インデックスを付けることで、後の操作をより速く実行できるようになります。  
  
 ![コード マップ&#45;メソッドと関連するフィールドを表示する](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  緑色の強調表示は、マップに追加された最後の項目を示します。 緑色の矢印は、コード内でのカーソルの位置を示します。 項目間の矢印は、さまざまな関係を表します。 マップの項目に関する詳細情報は、項目の上にマウスを移動してツールヒントを調べることで確認できます。  
  
 ![コード マップ&#45;ツールヒントの表示](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## <a name="navigate-and-examine-code-from-the-map"></a>マップからコードを移動して調査する  
 各フィールドのコード定義を表示するには、フィールド マップをダブルクリックまたはフィールドとキーを押して選択**F12**します。 緑色の矢印がマップの項目間を移動します。 コード エディターのカーソルも自動的に移動します。  
  
 ![コード マップ&#45;フィールド定義の確認](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![コード マップ&#45;フィールド定義の確認](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  また、コード エディターでカーソルを動かすと、マップの緑色の矢印を移動できます。  
  
## <a name="understand-relationships-between-pieces-of-code"></a>コード間のリレーションシップを把握する  
 ここで、他のどのコードが `history` フィールドおよび `paintObjects` フィールドとやり取りしているのかを把握する必要があります。 これらのフィールドを参照するすべてのメソッドをマップに追加できます。 この操作は、マップまたはコード エディターから行うことができます。  
  
 ![コード マップ&#45;すべての参照の検索](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![コード エディターからコード マップを開く](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Windows Phone や Windows ストアなどの複数のアプリで共有されるプロジェクトから項目を追加すると、それらの項目は常に、現在アクティブなアプリ プロジェクトと共にマップに表示されます。 そのため、コンテキストを別のアプリ プロジェクトに変更すると、マップ上のコンテキストも、共有プロジェクトから新たに追加した項目に変更されます。 マップ上の項目に実行する操作は、同じコンテキストを共有する項目にのみ適用されます。  
  
 関係のフローを再配置してマップを読みやすくするために、レイアウトを変更します。 項目をドラッグすることにより、マップ上で項目を移動することもできます。  
  
 ![コード マップ&#45;レイアウトの変更](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  既定では、**インクリメンタル レイアウト**がオンにします。 この設定では、新しい項目の追加時にマップの再配置は最小限に抑えられます。 新しい項目を追加するたびに、マップ全体を再配置、オフにする。**インクリメンタル レイアウト**します。  
  
 ![コード マップ&#45;レイアウトの変更](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 これらのメソッドを調べます。 マップをダブルクリックします、 **PaintCanvas**メソッド、またはこのメソッド、およびキーを押して選択**F12**します。 このメソッドにより、`history` と `paintObjects` が空のリストとして作成されることがわかります。  
  
 ![コード マップ&#45;メソッド定義の確認](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 ここで、同じ手順を繰り返して、`clear` メソッドの定義を調べます。 `clear` が `paintObjects` と `history`を使用して一部のタスクを実行することがわかります。 次に、このメソッドは `Repaint` メソッドを呼び出します。  
  
 ![コード マップ&#45;メソッド定義の確認](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 ここで、`addPaintObject` メソッドの定義を調べます。 このメソッドも、`history` と `paintObjects` を使用して一部のタスクを実行します。 また、このメソッドは `Repaint` を呼び出します。  
  
 ![コード マップ&#45;メソッド定義の確認](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## <a name="find-the-problem-by-examining-the-map"></a>マップを調べて問題を見つける  
 `history` と `paintObjects` を変更するすべてのメソッドが `Repaint` を呼び出すと考えられます。 ただし、`undo` メソッドは `Repaint` を呼び出しませんが、`undo` メソッドは同じフィールドを変更します。 したがって、`Repaint` で `undo` を呼び出すことにより、この問題を解決できると考えられます。  
  
 ![コード マップ&#45;検索が欠落しているメソッド呼び出し](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 この失われている呼び出しを示すマップがない場合、特にコードが複雑になると、この問題を見つけることがより困難になる可能性があります。  
  
## <a name="share-your-discovery-and-next-steps"></a>探索と次のステップを共有する  
 自分または他のユーザーがこのバグを修正する前に、問題と問題の解決方法に関するメモをマップに記載できます。  
  
 ![コード マップ&#45;フォロー アップのためのコメントとフラグ項目](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 たとえば、マップにコメントを追加し、色を使用して項目にフラグを設定できます。  
  
 ![コード マップ&#45;コメントとフラグが設定されたアイテム](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Microsoft Outlook をインストール済みの場合は、他のユーザーに電子メールでマップを送信できます。 マップをイメージまたはその他の形式でエクスポートすることもできます。  
  
 ![コード マップ&#45;共有、エクスポート、メール](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## <a name="fix-the-problem-and-show-what-you-did"></a>問題を修正して操作内容を表示する  
 このバグを修正するには、`Repaint`に `undo` の呼び出しを追加します。  
  
 ![コード マップ&#45;不足しているメソッドの呼び出しを追加](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 修正を確認するには、デバッグ セッションを再開して、バグの再現を試みます。 今すぐ選択**最後のストロークを元に戻す**期待どおりに動作し、正しい修正が行われたことを確認します。  
  
 ![コード マップ&#45;確認コードを修正](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 マップを更新すると、実行した修正を示すことができます。  
  
 ![コード マップ&#45;メソッドの呼び出しが不足している更新マップ](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 マップに間のリンクが表示されます**を元に戻す**と**を再描画**します。  
  
 ![コード マップ&#45;メソッドの呼び出しで更新されたマップ](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  マップを更新するときに、マップの作成に使用したコード インデックスが更新されたことを示すメッセージが表示される場合があります。 これは、他のだれかがコードを変更し、マップが現在のコードに一致しなくなっていることを意味します。 このことでマップの更新が停止されることはありませんが、コードとの一致を確認するためにマップを作成し直すことが必要になる場合があります。  
  
 これで調査が終了しました。 コードのマップにより、問題を正常に検出して修正しました。 また、コード内を移動することや確認したことの記憶に役立ち、問題を解決するための手順を示すマップも備わりました。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ中に呼び出し履歴に対するメソッドをマップします。](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [コードの視覚化](../modeling/visualize-code.md)



