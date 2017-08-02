---
title: "Visual Studio でのデバッグ中に呼び出し履歴に対するメソッドのマップ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ab08446140608a65b6894b3015c52227040611fd
ms.lasthandoff: 02/22/2017

---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio でデバッグを行うときの呼び出し履歴に対するメソッドのマップ
デバッグ中に呼び出し履歴を視覚的にトレースするためのコード マップを作成します。 コメントをマップに追加することでバグの発見に重点を置いてコードの動作を追跡できます。  
  
 ![呼び出し履歴コード マップを使用したデバッグ](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")  
  
 要件:  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   デバッグできるコード (Visual C# .NET、Visual Basic .NET、C++、JavaScript、X++ など) です。  
  
 参照:[ビデオ: コード マップ デバッガーの統合 (チャネル 9) で視覚的にデバッグ](http://go.microsoft.com/fwlink/?LinkId=293418)•[呼び出し履歴でマップ](#MapStack)•[コードに関するメモを作成](#MakeNotes)•[次の呼び出し履歴でマップを更新](#UpdateMap)•[マップに関連するコードを追加](#AddRelatedCode)•[マップを使用してバグを検索](#FindBugs)• [Q & A](#QA)  
  
 コマンドとコード マップを使用する場合に使用できる操作の詳細については、「[参照およびコード マップの再配置](../modeling/browse-and-rearrange-code-maps.md)します。  
  
##  <a name="a-namemapstacka-map-the-call-stack"></a><a name="MapStack"></a>呼び出し履歴でマップします。  
  
1.  デバッグを開始します。 (キーボード: **f5 キーを押して**)  
  
2.  後でアプリが中断モードになるか、関数にステップ イン、**コード マップ**します。 (Keyboard: **Ctrl** + **Shift** + **`**)  
  
     ![呼び出し履歴のマッピングを開始するコード マップを選択して](~/debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")  
  
     現在の呼び出し履歴は新しいコード マップ上にオレンジ色で表示されます。  
  
     ![確認の呼び出し履歴コード マップを](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")  
  
     デバッグを継続している間、マップは自動的に更新されます。 参照してください[次の呼び出し履歴でマップを更新](#UpdateMap)します。  
  
##  <a name="a-namemakenotesa-make-notes-about-the-code"></a><a name="MakeNotes"></a>コードに関するメモを作成します。  
 コードの動作を追跡するためのコメントを追加します。 新しい行をコメントを追加するキーを押して**shift + return**します。  
  
 ![コード マップの呼び出し履歴にコメントを追加](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")  
  
##  <a name="a-nameupdatemapa-update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a>次の呼び出し履歴でマップを更新  
 アプリを次のブレークポイントまで実行するか、関数にステップ インします。 マップに新しい呼び出し履歴が追加されます。  
  
 ![次の呼び出し履歴でコード マップを更新](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")  
  
##  <a name="a-nameaddrelatedcodea-add-related-code-to-the-map"></a><a name="AddRelatedCode"></a>マップに関連するコードを追加します。  
 マップを作成できたところで、次の作業に進みます。 Visual C# .NET または Visual Basic .NET で作業している場合は、フィールド、プロパティ、およびその他のメソッドなどの項目を追加して、コードの動作を追跡します。  
  
 メソッドのコード定義を表示するには、そのメソッドをダブルクリックするか、そのメソッドのショートカット メニューを使用します。 (キーボード: マップとキーを押してに関する方法を選択して**F12**)  
  
 ![コード マップ上のメソッドのコード定義へ移動](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")  
  
 マップで追跡する項目を追加します。  
  
 ![メソッドの呼び出し履歴コード マップのフィールドを表示する](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")  
  
> [!NOTE]
>  既定では、マップに項目を追加すると、クラス、名前空間、アセンブリなどの親グループのノードも追加されます。 これは便利ですが、するおくと、マップ単純なを使用してこの機能をオフにする、**親を含める**ボタン マップ ツールバーで、またはキーを押して**ctrl キーを押し**項目を追加するとします。  
  
 ![呼び出し履歴コード マップ上のメソッドに関連するフィールド](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")  
  
 ここでは、同じフィールドを使用するメソッドを簡単に表示できます。 追加された最新の項目は緑色で表示されます。  
  
 コードのさらに多くの項目を表示するには、マップの作成を続けます。  
  
 ![フィールドを使用するメソッドを参照: 呼び出し履歴コード マップ](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")  
  
 ![呼び出し履歴コード マップのフィールドを使用するメソッド](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")  
  
##  <a name="a-namefindbugsa-find-bugs-using-the-map"></a><a name="FindBugs"></a>マップを使用してバグを発見します。  
 コードの視覚化はバグをよりすばやく見つけるために役立ちます。 たとえば、描画プログラムのバグを調査しているとします。 直線を描画して元に戻そうとしても、別の直線を描画するまで何も起こりません。  
  
 そのため、`clear`、`undo`、および `Repaint` メソッドにブレークポイントを設定し、デバッグを開始して、次のようなマップを作成します。  
  
 ![別の呼び出し履歴コード マップに追加](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")  
  
 マップ上のすべてのユーザー ジェスチャーが、`Repaint` を除いて、`undo` を呼び出していることがわかります。 この動作が原因で `undo` がすぐに実行されない可能性があります。  
  
 バグを修正してプログラムの実行を続けると、マップに `undo` から `Repaint` への新しい呼び出しが追加されます。  
  
 ![コード マップに新しいメソッドの呼び出しごとにスタックに追加](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")  
  
##  <a name="a-nameqaa-q--a"></a><a name="QA"></a> Q & A  
  
-   **すべての呼び出しは、マップに表示されます。その理由を教えてください。**  
  
     既定では、ユーザー自身のコードだけがマップに表示されます。 外部コードを表示するを有効にすること、**呼び出し履歴**ウィンドウ。  
  
     ![呼び出し履歴 ウィンドウを使用して外部のコードを表示](~/debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")  
  
     オンまたはオフ**マイ コードのみを有効にする**デバッグ オプションを Visual Studio で。  
  
     ![[オプション] ダイアログを使用して外部コードの表示](~/debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")  
  
-   **コードが影響マップを変更しますか。**  
  
     マップを変更してもコードは何も影響を受けません。 マップでの名前変更、移動、削除は自由に行うことができます。  
  
-   **このメッセージはどういう:「ダイアグラムは古いバージョンのコードに基づいている可能性があります」でしょうか。**  
  
     マップを最後に更新してからコードが変更されている可能性があります。 たとえば、マップ上の呼び出しがコードに存在しなくなった可能性があります。 メッセージを閉じてから、マップを再び更新する前にソリューションをリビルドしてみます。  
  
-   **マップのレイアウトを制御する方法は?**  
  
     開いている、**レイアウト**マップのツールバー メニュー。  
  
    -   既定のレイアウトを変更します。  
  
    -   オフにする、マップを自動的に再配置を停止する**デバッグ時に自動レイアウト**します。  
  
    -   オフにする項目を追加する場合は、できるだけのマップを再配置、**インクリメンタル レイアウト**します。  
  
-   **マップを他のユーザーと共有できますか。**  
  
     マップをエクスポートし、Microsoft Outlook があれば、他のユーザーに送信できます。または、マップを独自のソリューションに保存し、Team Foundation バージョン管理にチェックインできます。  
  
     ![他のユーザーと呼び出し履歴コード マップを共有](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")  
  
-   **マップに新しい呼び出し履歴を自動的に追加されないを停止する方法は?**  
  
     選択![ ボタン - コードで呼び出し履歴を表示するマップを自動的に](~/debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon")マップのツールバー。 マップを現在の呼び出し履歴を手動で追加するには、キーを押して**Ctrl** + **shift キーを押し** + **`**します。  
  
     マップでは引き続き、デバッグ中にマップ上の既存の呼び出し履歴が強調表示されます。  
  
-   **項目のアイコンと矢印どういう意味でしょうか。**  
  
     項目に関する詳細を取得するには、その項目の上にマウス ポインターを移動し、アイテムのヒントを確認します。 検索することも、**凡例**を各アイコンの意味を参照してください。  
  
     ![呼び出し履歴コード マップ上のアイコンの意味] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")  
  
 参照:[呼び出し履歴でマップ](#MapStack)•[コードに関するメモを作成](#MakeNotes)•[次の呼び出し履歴でマップを更新](#UpdateMap)•[マップに関連するコードを追加](#AddRelatedCode)•[マップを使用してバグを検索](#FindBugs)  
  
## <a name="see-also"></a>関連項目  
 [複数のソリューション間の依存関係を対応します。](../modeling/map-dependencies-across-your-solutions.md)   
 [コード マップを使ったアプリケーションのデバッグ](../modeling/use-code-maps-to-debug-your-applications.md)   
 [コード マップ アナライザーを使った潜在的な問題を検索します。](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [コード マップの参照および再配置](../modeling/browse-and-rearrange-code-maps.md)
