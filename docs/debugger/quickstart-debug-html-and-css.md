---
title: "HTML および CSS (UWP と Windows 8.1 アプリ) のデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.DomExplorer
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
ms.assetid: 6d156cff-36c6-425a-acf8-e1f02d4f7869
caps.latest.revision: "101"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: bf9049907d1648b1950f8d66e0fd183c82699e92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debug-html-and-css-in-uwp-and-windows-81-apps"></a>HTML および CSS UWP と Windows 8.1 アプリをデバッグします。
![Windows と Windows Phone に適用](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Visual Studio では、JavaScript アプリに総合的なデバッグ機能が用意されており、Internet Explorer および Visual Studio の開発者には使い慣れた機能が含まれています。 これらの機能はサポートされて[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]、Windows Phone アプリでは、Apache Cordova の Visual Studio Tools を使用して作成されたアプリ。  
  
 DOM 検査ツールが提供する対話式のデバッグ モデルを使用すると、レンダリングされる HTML および CSS のコードを表示および変更できます。 これらはすべてデバッガーを停止して再起動することなく実行できます。
  
 その他の JavaScript のデバッグ、JavaScript コンソール ウィンドウの使用やブレークポイントの設定などの機能の詳細については「[クイック スタート: JavaScript のデバッグ](../debugger/quickstart-debug-javascript-using-the-console.md)と[Visual Studio でアプリのデバッグ](../debugger/debug-store-apps-in-visual-studio.md)です。  
  
##  <a name="InspectingDOM"></a> ライブ DOM の検査  
 DOM Explorer ではレンダリングされるページのビューが示され、DOM Explorer を使用すると値を変更して結果をすぐに確認できます。 これにより、デバッガーを停止して再起動することなく変更をテストできます。 この方法でページと対話するときはプロジェクトのソース コードは変更されないので、必要なコード修正が見つかったら、ソース コードを変更します。  
  
> [!TIP]
>  ソース コードを変更する際、デバッガーの停止や再起動を避けるために、[デバッグ] ツール バーの **[Windows アプリケーションの更新]** ボタンを使用して (または F4 キーを押して) アプリケーションを更新できます。 詳細については、次を参照してください。[アプリを更新する (JavaScript)](../debugger/refresh-an-app-javascript.md)です。  
  
 DOM Explorer を使用すると次のことができます。  
  
-   DOM 要素のサブツリー内を移動し、レンダリングされる HTML、CSS、および JavaScript コードを調査します。  
  
-   レンダリングされる要素の属性および CSS スタイルを動的に編集し、結果をすぐに確認します。  
  
-   CSS スタイルがページ要素に適用される方法を調査し、適用されたルールをトレースします。  
  
 アプリケーションをデバッグするときは、しばしば DOM Explorer で要素を選択する必要があります。 要素を選択すると、DOM Explorer の右側のタブに表示される値が、DOM Explorer での要素の選択を反映して自動的に更新されます。 このようなタブとしては、 **[スタイル]**、 **[計算済み]**、 **[レイアウト]**があります。 UWP アプリをサポートしても、**イベント**と**変更**タブです。 要素の選択の詳細については、「 [Selecting elements](#SelectingElements)」を参照してください。  
  
> [!TIP]
>  閉じた DOM Explorer ウィンドウを再び開くには、 **[デバッグ]**>**[ウィンドウ]** > **[DOM Explorer]** の順に選びます。 このウィンドウは、スクリプトのデバッグ セッション中にのみ表示されます。  
  
 次の手順では、DOM Explorer を使用してアプリを対話的にデバッグするプロセスを実行します。 `FlipView` コントロールを使用するアプリケーションを作成した後、それをデバッグします。 アプリケーションには複数のエラーが含まれています。  
  
> [!WARNING]
>  次のサンプル アプリは、UWP アプリです。 Cordova でも同じ機能がサポートされていますが、アプリは異なります。  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>次の方法で、ライブ DOM を検査することによってデバッグします。  
  
1.  Visual Studio で **[ファイル]** > **[新しいプロジェクト]**」を参照してください。  
  
2.  選択**JavaScript** > **ストア**、いずれかを選択**Windows アプリ**または**Windows Phone アプリ**をクリックして**空のアプリ**です。  
  
3.  `FlipViewApp`などのプロジェクトの名前を入力し、 **[OK]** を選んでアプリを作成します。  
  
4.  default.html の BODY 要素に、次のコードを追加します。  
  
    ```html  
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
             style="display:none">  
        <div class="fixedItem" >  
            <img src="#" data-win-bind="src: flipImg" />  
        </div>  
    </div>  
    <div id="fView" style="width:100px;height:100px"  
        data-win-control="WinJS.UI.FlipView" data-win-options="{  
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
    </div>  
    ```  
  
5.  default.css を開き、次の CSS を追加します。  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 100%;  
        width: 100%;  
        margin: 25%;  
    }  
    ```  
  
6.  default.js のコードを、次のコードに置き換えます。  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var myData = [];  
        for (var x = 0; x < 4; x++) {  
            myData[x] = { flipImg: "/images/logo.png" }  
        };  
  
        var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !==  
                activation.ApplicationExecutionState.terminated) {  
                    // TODO: . . .  
                } else {  
                    // TODO: . . .  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                updateImages();  
            }  
        };  
  
        function updateImages() {  
  
            pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
            pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
            pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var publicMembers = {  
            items: pages  
        };  
  
        WinJS.Namespace.define("Data", publicMembers);  
  
    })();  
    ```  
  
     このアプリを Phone エミュレーター (シミュレーターと同様の外観になります) で実行すると、次の図に示すようになります。 ただし、アプリをこの状態にするには、まず、多数のバグを修正する必要があります。  
  
     ![期待される結果を表示する FlipView アプリ](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")  
  
7.  **[デバッグ]** ツール バーの **[デバッグの開始]** ボタンの横にあるドロップダウン リストの **[シミュレーター]** または **[Emulator 8.1 WVGA 4 inch 512MB] (エミュレーター 8.1 WVGA 4 インチ 512 MB)** をクリックします。  
  
     ![デバッグ ターゲット リスト](../debugger/media/js_select_target.png "JS_Select_Target")  
  
8.  **[デバッグ]** > **Start [デバッグ]ging**の順にクリックするか、F5 キーを押して、デバッグ モードでアプリを実行します。  
  
     これによりアプリはシミュレーターまたは Phone エミュレーターで実行されますが、スタイリングにはいくつかバグがあるため、画面にはほとんど何も表示されません。 最初の `FlipView` のイメージが、画面の中央の小さい四角形に表示されます。  
  
9. アプリをシミュレーターで実行している場合は、シミュレーターの右側にある **[解像度の変更]** ツール バー コマンドをクリックし、画面の解像度を 1280 x 800 に構成します。 これによって、次の手順で示される値がシミュレーターに表示される値と一致することが確認できます。  
  
10. Visual Studio に切り替え、 **[DOM Explorer]** タブをクリックします。  
  
    > [!TIP]
    >  Alt + Tab キーまたは F12 キーを押すと、Visual Studio と実行中のアプリを切り替えることができます。  
  
11. DOM Explorer ウィンドウで、ID が `"fView"`であるセクションの DIV 要素を選択します。 方向キーを使用して、正しい DIV 要素を表示して選択します。 (右方向キーにより、要素の子を表示する。)  
  
     ![DOM Explorer](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    >  」と入力して、JavaScript コンソール ウィンドウの左下隅の DIV 要素を選択することも`select(fView)`で、>> の入力プロンプトとし、Enter キーを押します。  
  
     DOM Explorer ウィンドウの右側のタブに表示される値が、DOM Explorer での現在の要素選択を反映して自動的に更新されます。  
  
12. 右側の **[計算済み]** タブをクリックします。  
  
     このタブは、選択した DOM 要素の各プロパティの、計算済みまたは最終の値を示します。  
  
13. 高さの CSS 規則を開きます。 100% に設定されての高さの値と矛盾して表示される 100 px に設定するインライン スタイルがあることに注意してください、 `#fView` CSS セレクター。 `#fView` セレクターの取り消し線テキストは、インライン スタイルがこのスタイルよりも優先されることを示しています。  
  
     **[計算済み]** タブを次の図に示します。  
  
     ![DOM エクスプ ローラーの計算済み タブ](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")  
  
14. DOM Explorer のメイン ウィンドウで、 `fView` DIV 要素の高さと幅のインライン スタイルをダブルクリックします。 ここで値を編集することができます。 このシナリオでは、これらを完全に削除する必要があります。  
  
15. `width: 100px;height: 100px;`を選択し、Del キー、Enter キーの順に押します。 デバッグ セッションを停止していなくても、Enter キーを押すとすぐに、新しい値がシミュレーターまたは Phone エミュレーターに反映されます。  
  
    > [!IMPORTANT]
    >  DOM Explorer ウィンドウで属性を更新できるように、 **[スタイル]**、 **[計算済み]**、 **[レイアウト]** の各タブに表示される値も更新できます。 詳細については、次を参照してください。 [DOM Explorer を使用して CSS のデバッグ スタイル](../debugger/debug-css-styles-using-dom-explorer.md)と[DOM Explorer を使用してデバッグ レイアウト](../debugger/debug-layout-using-dom-explorer.md)です。  
  
16. シミュレーターまたは Phone エミュレーターを選択するか、または Alt + Tab キーを使って、アプリケーションに切り替えます。  
  
     これで、 `FlipView` コントロールがシミュレーターまたは Phone エミュレーターの画面を超えるサイズで表示されます。 これは意図した結果ではありません。 Visual Studio に戻って、調査します。  
  
17. DOM Explorer で、 **[計算済み]** タブを再度クリックし、高さの規則を開きます。 fView 要素は、CSS から予想されるように 100% の値を示したままですが、計算済みの値はシミュレーターの画面の高さと等しく (たとえば、800px または 667.67px)、このアプリで必要な高さではありません。 調査するために、 `fView` DIV 要素の高さと幅を削除することができます。  
  
18. **[スタイル]** タブで、 `#fView` CSS セレクターの高さと幅のプロパティのチェックボックスをオフにします。  
  
     **[計算済み]** タブでは、高さは 400px と表示されています。 これによると、この値が、プラットフォーム CSS ファイルである ui-dark.css で指定された .win-flipview セレクターによるものであることを示しています。  
  
19. アプリケーションに切り替えます。  
  
     これで状況は改善されました。 しかし、なお修正する必要がある問題があります。それは余白が大きすぎることです。  
  
20. 調査のため、Visual Studio に切り替えをクリックし、**レイアウト** タブ、要素のボックス モデルを確認します。  
  
     **[レイアウト]** タブに、次の値が表示されます。  
  
    -   シミュレーターの場合は、320px (オフセット) および 320px (余白) です。  
  
    -   Phone エミュレーターの場合は、100px (オフセット) および 100px (余白) です。  
  
     次の図は、Phone エミュレーター (100px オフセットおよび余白) を使用する場合の **[レイアウト]** タブを示しています。  
  
     ![DOM Explorer の [レイアウト] タブ](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")  
  
     これは正しくありません。 **[計算済み]** タブでも、同じ余白の値が表示されます。  
  
21. **[スタイル]** タブをクリックし、 `#fView` CSS セレクターを検索します。 ここでは、 **"余白"** プロパティに 25% の値が表示されます。  
  
22. 25% を選択して、それを 25px に変更し、Enter キーを押します。  
  
23. また、 **[スタイル]** タブで .win-flipview セレクターの高さの規則をクリックして、400px を 500px に変更し、Enter キーを押します。  
  
24. アプリケーションに戻ると、要素の配置が正しい状態で表示されます。 デバッガーを停止したり再起動したりせずに、ソースを修正してアプリケーションを再表示するには、次の手順を参照してください。  
  
#### <a name="to-refresh-your-app-while-debugging"></a>デバッグ中にアプリを更新するには  
  
1.  アプリケーションがまだ実行している間に、Visual Studio に切り替えます。  
  
2.  default.html を開き、 `"fView"` DIV 要素の高さと幅を 100% に変更して、ソース コードを変更します。  
  
3.  [デバッグ] ツール バーの **[Windows アプリケーションの更新]** ボタンをクリックします (または、F4 キーを押します)。 次のように、ボタンの外観:![アプリの Windows の更新ボタン](../debugger/media/js_refresh.png "JS_Refresh")です。  
  
     アプリのページが再読み込みされ、シミュレーターまたは Phone エミュレーターが前面に戻ります。  
  
     更新機能の詳細については、次を参照してください。[アプリを更新する (JavaScript)](../debugger/refresh-an-app-javascript.md)です。  
  
##  <a name="SelectingElements"></a> Selecting elements  
 アプリケーションをデバッグするときに、次の 3 種類の方法で DOM 要素を選択できます。  
  
-   直接 DOM エクスプローラー ウィンドウの要素をクリックする (または方向キーを使用)。  
  
-   **[要素の選択]** ボタン (Ctrl + B キー) を使用する。  
  
-   使用して、`select`は 1 つのコマンドの[JavaScript コンソール コマンド](../debugger/javascript-console-commands.md)です。  
  
 DOM Explorer のウィンドウを使用して要素を選択するときに、要素にマウス ポインターを置くと、対応する要素が実行しているアプリで強調表示されます。 これを行うには、DOM Explorer の要素をクリックして選択する必要があります。または、方向キーを使用して、要素を強調表示して選択できます。 **[要素の選択]** ボタンを使用して DOM Explorer の要素を選択することもできます。 次の図は、 **[要素の選択]** ボタンを示しています。  
  
 ![DOM Explorer で要素の ボタンを選択](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")  
  
 **[要素の選択]** をクリックする (または Ctrl + B キーを押す) と、実行しているアプリの項目をクリックすることにより、DOM Explorer で項目を選択できるように選択モードが変更されます。 1 回クリックすると、通常の選択モードに戻ります。 **[要素の選択]**をクリックすると、アプリが前面に表示され、カーソルが新しい選択モードを反映した形状に変わります。 アウトラインが表示された要素をクリックすると、DOM Explorer が前面に戻り、指定した要素が選択されています。  
  
 **[要素の選択]**をクリックする前に、 **[Display web page highlights] (Web ページの強調表示を表示)** を切り替えて実行しているアプリの要素を強調表示するかどうかを指定できます。 次の図は、このボタンを示しています。 強調表示は、既定で表示されます。  
  
 ![Web ページを表示 ボタンがハイライト](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")  
  
 強調表示する要素を選択する場合、シミュレーターでマウス ポインターを置く要素が強調表示されます。 強調表示された要素の色は、DOM Explorer の **[レイアウト]** タブに表示されるボックス モデルと一致します。  
  
> [!NOTE]
>  Windows Phone エミュレーターは、マウス ポインターを置くことによる要素の強調表示を部分的にサポートします。  
  
 使用して要素を選択する方法を示す例については、 **Select 要素**ボタンをクリックしを参照してください[DOM Explorer を使用して CSS のデバッグ スタイル](../debugger/debug-css-styles-using-dom-explorer.md)です。  
  
##  <a name="BrowserSupport"></a> ブラウザーとプラットフォームのサポート  
 JavaScript 用の Visual Studio ツールである DOM Explorer と JavaScript コンソール ウィンドウは、次のプラットフォーム上でサポートされます。  
  
-   [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]Windows Phone アプリの JavaScript と HTML を使った  
  
-   [!INCLUDE[win81](../debugger/includes/win81_md.md)]  
  
-   [!INCLUDE[win8](../debugger/includes/win8_md.md)]  
  
 [と Visual Studio をダウンロードするには、](http://go.microsoft.com/fwlink/?LinkID=232448) ここ [!INCLUDE[win8](../debugger/includes/win8_md.md)] にアクセスしてください。  
  
## <a name="see-also"></a>参照  
 [Debug apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [DOM Explorer を使用して CSS スタイルをデバッグします。](../debugger/debug-css-styles-using-dom-explorer.md)   
 [DOM Explorer を使用して、レイアウトをデバッグします。](../debugger/debug-layout-using-dom-explorer.md)   
 [DOM イベント リスナーの表示](../debugger/view-dom-event-listeners.md)   
 [アプリを更新する (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [WebView コントロールをデバッグします。](../debugger/debug-a-webview-control.md)   
 [キーボード ショートカット](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [JavaScript コンソール コマンド](../debugger/javascript-console-commands.md)   
 [HTML、CSS、および JavaScript サンプル コードをデバッグします。](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [製品のサポートとアクセシビリティ](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)