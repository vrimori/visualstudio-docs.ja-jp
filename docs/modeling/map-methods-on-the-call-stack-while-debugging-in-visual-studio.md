---
title: Visual Studio でデバッグを行うときの呼び出し履歴に対するメソッドのマップ
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 111a1180f694b57a4e5ae013a41128a4a7e9e9f5
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748687"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio でデバッグを行うときの呼び出し履歴に対するメソッドのマップ
コード マップをデバッグしながら呼び出し履歴を視覚的にトレースを作成します。 コメントをマップに追加することでバグの発見に重点を置いてコードの動作を追跡できます。

 ![コード マップの呼び出し履歴を使用したデバッグ](../debugger/media/debuggermap_overview.png)

 要件:

-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

-   Visual c#、Visual Basic など、C++、JavaScript、x++ をデバッグするコード

 参照トピック

-   [ビデオ: コード マップ デバッガーの統合 (チャネル 9) を使用してデバッグ視覚的に](http://go.microsoft.com/fwlink/?LinkId=293418)

-   [呼び出し履歴でマップします。](#MapStack)

-   [コードに関するメモします。](#MakeNotes)

-   [次の呼び出し履歴でマップを更新](#UpdateMap)

-   [マップに関連するコードを追加します。](#AddRelatedCode)

-   [マップを使用してバグを発見します。](#FindBugs)

-   [Q &AMP; A](#QA)

 コマンドおよびコード マップを操作するときに使用できるアクションの詳細については、「[参照およびコード マップの再配置](../modeling/browse-and-rearrange-code-maps.md)です。

##  <a name="MapStack"></a> 呼び出し履歴でマップします。

1.  デバッグを開始します。 (キーボード: **f5 キーを押して**)

2.  後でアプリが中断モードに入るか、関数にステップ イン、**コード マップ**です。 (キーボード: **Ctrl** + **Shift** + **`**)

     ![コード マップを選択して呼び出し履歴のマッピングを開始](../debugger/media/debuggermap_choosecodemap.png)

     現在の呼び出し履歴は新しいコード マップ上にオレンジ色で表示されます。

     ![コード マップの呼び出し履歴を参照](../debugger/media/debuggermap_seeundocallstack.png)

     デバッグを継続している間、マップは自動的に更新されます。 参照してください[次の呼び出し履歴でマップを更新](#UpdateMap)です。

##  <a name="MakeNotes"></a> コードに関するメモします。
 コードで何が起こっているかを追跡するためにコメントを追加します。 新しい行をコメントを追加するキーを押して**shift + return**です。

 ![コード マップの呼び出し履歴にコメントを追加](../debugger/media/debuggermap_addcomment.png)

##  <a name="UpdateMap"></a> 次の呼び出し履歴でマップを更新
 アプリを次のブレークポイントまで実行するか、関数にステップ インします。 マップに新しい呼び出し履歴が追加されます。

 ![次の呼び出し履歴でコード マップを更新](../debugger/media/debuggermap_addclearcallstack.png)

##  <a name="AddRelatedCode"></a> マップに関連するコードを追加します。
 作成できたところで、マップの新機能 次へしますか。 C# または Visual Basic で作業している場合は、フィールド、プロパティ、およびコードで何が起こっているかを追跡するために、他の方法などのアイテムを追加します。

 メソッドのコード定義を表示するには、そのメソッドをダブルクリックするか、そのメソッドのショートカット メニューを使用します。 (キーボード: マップとキーを押す方法を選択して**F12**)

 ![コード マップのメソッドのコード定義に移動](../debugger/media/debuggermap_gotocodedefinition.png)

 マップで追跡する項目を追加します。

 ![呼び出し履歴コード マップのメソッドのフィールドを表示](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
>  既定では、マップに項目を追加すると、クラス、名前空間、アセンブリなどの親グループのノードも追加されます。 これは便利です、できます簡潔にマップを使用して、この機能を無効にして、**親を含める**ボタン、マップ ツールバーで、またはキーを押して**ctrl キーを押し**項目を追加するとします。

 ![呼び出し履歴コード マップのメソッドに関連するフィールド](../debugger/media/debuggermap_showedfields.png)

 ここでは、同じフィールドを使用するメソッドを簡単に表示できます。 追加された最新の項目は緑色で表示されます。

 コードのさらに多くの項目を表示するには、マップの作成を続けます。

 ![フィールドを使用するメソッドを参照: 呼び出し履歴コード マップ](../debugger/media/debuggermap_findallreferences.png)

 ![呼び出し履歴コード マップのフィールドを使用するメソッド](../debugger/media/debuggermap_foundallreferences.png)

##  <a name="FindBugs"></a> マップを使用してバグを発見します。
 コードの視覚化はバグをよりすばやく見つけるために役立ちます。 たとえば、描画プログラムでバグを調査するいるとします。 直線を描画して元に戻そうとしても、別の直線を描画するまで何も起こりません。

 そのため、`clear`、`undo`、および `Repaint` メソッドにブレークポイントを設定し、デバッグを開始して、次のようなマップを作成します。

 ![コード マップに別の呼び出し履歴を追加](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 マップ上のすべてのユーザー ジェスチャーが、`Repaint` を除いて、`undo` を呼び出していることがわかります。 これは、理由を説明する可能性があります`undo`すぐに機能しません。

 バグを修正してプログラムの実行を続けると、マップに `undo` から `Repaint` への新しい呼び出しが追加されます。

 ![コード マップの呼び出し履歴に新しいメソッド呼び出しを追加](../debugger/media/debuggermap_addnewcallforrepaint.png)

##  <a name="QA"></a> Q & A

-   **すべての呼び出しは、マップに表示されます。その理由を教えてください。**

     既定では、ユーザー自身のコードだけがマップに表示されます。 外部コードを表示するには、オン、**呼び出し履歴**ウィンドウ。

     ![[呼び出し履歴] ウィンドウを使用して外部コードを表示](../debugger/media/debuggermap_callstackmenu.png)

     オンまたはオフ**マイ コードのみを有効にする**デバッグ オプションの Visual studio:

     ![[オプション] ダイアログ ボックスを使用して、外部コードを表示](../debugger/media/debuggermap_debugoptions.png)

-   **コードに影響のマップを変更しますか。**

     マップを変更すると、任意の方法でコードが影響しません。 マップでの名前変更、移動、削除は自由に行うことができます。

-   **このメッセージはどういう:「ダイアグラムは古いバージョンのコードに基づく可能性があります」しますか?**

     マップを最後に更新してからコードが変更されている可能性があります。 たとえば、マップ上の呼び出しがコードに存在しなくなった可能性があります。 メッセージを閉じてから、マップを再び更新する前にソリューションをリビルドしてみます。

-   **マップのレイアウトを制御する方法は?**

     開く、**レイアウト**マップ ツールバーのメニュー。

    -   既定のレイアウトを変更します。

    -   オフにするマップを自動的に再配置を停止する**デバッグ時に自動レイアウト**です。

    -   オフに並べ替えるには最小限に抑え、マップ項目を追加するときに、**インクリメンタル レイアウト**です。

-   **他のユーザーとマップを共有できますか。**

     マップをエクスポートし、Microsoft Outlook があれば、他のユーザーに送信できます。または、マップを独自のソリューションに保存し、Team Foundation バージョン管理にチェックインできます。

     ![呼び出し履歴コード マップを他のユーザーと共有](../debugger/media/debuggermap_sharewithothers.png)

-   **新しい呼び出し履歴を自動的に追加したマップを停止する方法は?**

     選択![ボタン&#45;ショー呼び出し履歴コード マップには自動的に](../debugger/media/debuggermap_automaticupdateicon.gif)マップ ツールバーでします。 マップを現在の呼び出し履歴を手動で追加するには、キーを押して**Ctrl** + **shift キーを押し** + **`** です。

     デバッグ中に、マップ上の既存の呼び出し履歴を強調表示、マップが続行されます。

-   **項目のアイコンと矢印の意味**

     詳細については、項目を取得するには、上にマウス ポインターを移動し、項目のツールヒントを確認します。 検索することも、**凡例**を各アイコンの意味を参照してください。

     ![呼び出し履歴コード マップのアイコンの意味](../debugger/media/debuggermap_showlegend.png)

 参照トピック

-   [呼び出し履歴でマップします。](#MapStack)

-   [コードに関するメモします。](#MakeNotes)

-   [次の呼び出し履歴でマップを更新](#UpdateMap)

-   [マップに関連するコードを追加します。](#AddRelatedCode)

-   [マップを使用してバグを発見します。](#FindBugs)

## <a name="see-also"></a>関連項目

- [ソリューション間の依存関係をマップする](../modeling/map-dependencies-across-your-solutions.md)
- [コード マップを使用してアプリケーションをデバッグする](../modeling/use-code-maps-to-debug-your-applications.md)
- [コード マップ アナライザーを使用して潜在的な問題を検索する](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [コード マップの参照および再配置](../modeling/browse-and-rearrange-code-maps.md)
