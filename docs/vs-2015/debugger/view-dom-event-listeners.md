---
title: DOM イベント リスナーの表示 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d6f5c913cb2868df1af25470eb69f84575ffab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223302"
---
# <a name="view-dom-event-listeners"></a>DOM イベント リスナーの表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows および Windows Phone に適用されます] (../Image/windows_and_phone_content.png"windows_and_phone_content")  
  
 **イベント**DOM Explorer のタブには、DOM 要素に関連付けられているイベントが表示されます。 各最上位のノードで、**イベント** タブをアクティブなサブスクライバーを持つイベントを表します。 最上位のノードには、特定のイベントのために登録されたイベント リスナーを表すサブノードが含まれます。 イベント リスナーの表示に加えて、このタブを使用して、JavaScript コード内のイベント リスナーの場所に移動できます。 このトピックの情報は、HTML および JavaScript を使用するストア アプリに適用します。  
  
 リスト、**イベント** タブは動的です。 アプリの実行中にイベント リスナーを追加すると、新しいイベント リスナーが一覧に表示されます。 追加とイベント リスナーの削除については、次を参照してください。[をイベント リスナーで問題を解決するためのヒント](#Tips)このトピックの「します。  
  
> [!NOTE]
>  イベント リスナーなど、DOM 要素でないコード要素の`xhr`に表示されない、**イベント**タブ。  
  
## <a name="view-event-listeners-for-dom-elements"></a>DOM 要素のイベント リスナーの表示  
 この例は、Windows Phone ストア アプリを示します。 ここで説明する DOM Explorer の機能は、Windows ストア アプリでもサポートされます。  
  
#### <a name="to-view-event-listeners"></a>イベント リスナーを表示するには  
  
1.  Visual Studio で、Windows Phone ピボット アプリケーション プロジェクト テンプレートを使用する JavaScript アプリを作成します。  
  
2.  テンプレートを Visual Studio で開いて、次のように選択します。 **4 in 512 MB のエミュレーター 8.1 WVGA**デバッガーでデバッグ ツールバーのドロップダウン リストで。  
  
     ![デバッグ対象を選択する](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
3.  F5 キーを押して、アプリをデバッグ モードで実行します。  
  
4.  実行中のアプリに移動、**セクション 3**ピボット テーブル アイテム。  
  
5.  Visual Studio に切り替えます (Alt + Tab キーまたは F12 キーを押します)。  
  
6.  DOM Explorer で、右上の [`Find`] を選択します。  
  
7.  「 `ListView`」と入力して Enter キーを押します。  
  
8.  必要に応じて、選択、 **[次へ]** を検索するボタン、`DIV`要素を表す、`ListView`コントロール (この要素には、`data-win-control`の値`WinJS.UI.ListView`)。  
  
     DOM Explorer で `DIV` 要素が選択された状態になります。  
  
9. 選択、**イベント**DOM エクスプ ローラーの右側にあるペインでタブ。  
  
     次に示すように、`DIV` 要素のアクティブ サブスクライバーがあるイベントが表示されます。  
  
     ![DOM Explorer の [イベント] タブ](../debugger/media/js-dom-events.png "JS_DOM_Events")  
  
10. これらのイベントのイベント リスナーに移動するには、関連付けられた JavaScript ファイルのリンクを選択します。  
  
11. DOM 階層の親要素のイベント リスナーを迅速に特定するには、DOM Explorer の下側にある階層リストの親要素を選択します。  
  
     ![DOM 階層で親要素を選択](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")  
  
     **イベント** タブには、階層リストで選択した任意の要素のイベント リスナーが表示されます。  
  
###  <a name="Tips"></a> イベント リスナーで問題を解決するためのヒント  
 一部のアプリのシナリオでイベント リスナーする必要があります明示的に削除するを使用して[removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)します。 使用して、**イベント**イベント リスナーは、コードの実行中に DOM 要素から削除されているかどうかをテストする DOM エクスプ ローラー タブ。 これらの問題の解決に役立つヒントを次に示します。  
  
-   Visual Studio で実装された単一ページ ナビゲーション モデルを使用するアプリの[プロジェクト テンプレート](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx)、通常、ページの一部である DOM 要素などのオブジェクトに登録されたイベント リスナーを削除する必要はありません。 このシナリオでは、DOM 要素およびその関連付けられたイベント リスナーの有効期間は同じであり、ガベージ コレクションが可能です。  
  
-   DOM 要素またはオブジェクトの有効期間が関連付けられたイベント リスナーと異なる場合には、`removeEventListener` メソッドを呼び出す必要があります。 たとえば、`window.onresize` イベントを使用する場合に、イベントを処理するページから離れるとイベント リスナーを削除しなければならない場合があります。  
  
-   `removeEventListener` が指定のリスナーを削除できなかった場合は、別のオブジェクトのインスタンスが呼び出された可能性があります。 使用することができます、 [bind メソッド (Function)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md)リスナーを追加するときに、この問題を解決するメソッド。  
  
-   いずれかを使用して追加されたイベント リスナーを削除する[bind メソッド (Function)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md)または匿名関数を使用して、リスナーを追加するときに、関数のインスタンスを格納します。 このパターンを安全に使用するための 1 つの方法を次に示します。  
  
    ```javascript  
    // You could use the following code within the constructor function of an object, or  
    // in the ready function of a PageControl object (Store app).  
    this.storedHandler = this._handlerFunc.bind(this);  
    elem.addEventListener('mouseup', this.storedHandler);  
  
    // In this example, add the following code in the PageControl object's unload function.  
    elem.removeEventListener('mouseup', this.storedHandler);  
  
    ```  
  
     バインドされた関数への参照を保存する代わりに次のコードを使用した場合、イベント リスナーを明示的に削除することはできなくなります。  
  
    ```javascript  
    // Avoid this pattern. No reference to the bound function is available.  
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));  
    ```  
  
-   `removeEventListener` のような `obj.on<eventname>` 属性を使用して追加した場合には、`window.onresize = handlerFunc` を使用してイベント リスナーを削除することはできません。  
  
-   JavaScript メモリ アナライザーを使用して[JavaScript メモリ](../profiling/javascript-memory.md)アプリ。 明示的に削除されたイベント リスナーは、メモリー リークとして表示されることがあります。  
  
## <a name="see-also"></a>関連項目  
 [クイック スタート: HTML と CSS をデバッグします。](../debugger/quickstart-debug-html-and-css.md)   
 [DOM Explorer を使用して CSS スタイルをデバッグします。](../debugger/debug-css-styles-using-dom-explorer.md)   
 [DOM Explorer を使用したレイアウトのデバッグ](../debugger/debug-layout-using-dom-explorer.md)



