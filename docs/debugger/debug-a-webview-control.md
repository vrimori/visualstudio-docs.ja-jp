---
title: "WebView コントロールのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# WebView コントロールのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Windows と Windows Phone に適用されます](~/docs/debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Windows Runtime アプリで `WebView` コントロールを検査しデバッグするには、アプリの開始時にスクリプト デバッガーをアタッチするよう Visual Studio を設定できます。  Visual Studio 2013 Update 2 から、デバッガーを使用して `WebView` コントロールと 2 つの方法で対話できます。  
  
-   `WebView` インスタンスで [DOM Explorer](../debugger/quickstart-debug-html-and-css.md) を開き、DOM 要素を検査し、CSS スタイルの問題を調査し、スタイルに対する動的な変更をテストします。  
  
-   [JavaScript コンソール](../debugger/javascript-console-commands.md) ウィンドウのターゲットとして、Web ページまたは `WebView` インスタンスで表示される `iFrame` を選択した後、コンソール コマンドを使用して Web ページとやり取りします。  コンソールは、現在のスクリプト実行コンテキストへのアクセスを提供します。  
  
### デバッガーのアタッチ \(C\#、Visual Basic、C\+\+\)  
  
1.  Visual Studio で、Windows Runtime アプリに `WebView` コントロールを追加します。  
  
2.  ソリューション エクスプローラーで、プロジェクトのショートカット メニューから **\[プロパティ\]** を選択して、プロジェクトのプロパティを開きます。  
  
3.  **\[デバッグ\]** をクリックします。  **\[アプリケーション プロセス\]** ボックスの一覧の **\[スクリプト\]** をクリックします。  
  
     ![スクリプト デバッガのアタッチ](../debugger/media/js_dom_webview_script_debugger.png "JS\_DOM\_WebView\_Script\_Debugger")  
  
4.  \(オプション\) Visual Studio の非 Express バージョンの場合、**\[ツール\]**、**\[オプション\]**、**\[デバッグ\]**、**\[Just\-In\-Time\]** をクリックして、スクリプトの JIT デバッグを無効にします。  
  
    > [!NOTE]
    >  JIT デバッグを無効にすると、一部の Web ページで生じる未処理の例外のダイアログ ボックスを非表示にできます。  Visual Studio Express では、JIT デバッグは常に無効となっています。  
  
5.  F5 キーを押してデバッグを開始します。  
  
### DOM Explorer を使って WebView コントロールを検査およびデバッグします。  
  
1.  \(C\#、Visual Basic、C\+\+\) スクリプト デバッガーをアプリにアタッチします。  手順については最初のセクションを参照してください。  
  
2.  まだ行っていない場合はアプリに `WebView` コントロールを追加して、F5 を押すとデバッグが開始します。  
  
3.  `Webview` コントロールが含まれるページに移動します。  
  
4.  **\[デバッグ」**、**\[ウィンドウ\]**、**\[DOM Explorer\]** をクリックして `WebView` コントロールの DOM Explorer ウィンドウを開き、検査する `WebView` の URL をクリックします。  
  
     ![DOM Explorer を開く](../debugger/media/js_dom_webview.png "JS\_DOM\_WebView")  
  
     `WebView` に関連付けられた DOM Explorer が Visual Studio の新しいタブとして表示されます。  
  
5.  [DOM Explorer を使用した CSS スタイルのデバッグ](../debugger/debug-css-styles-using-dom-explorer.md) で説明されているように、ライブ DOM 要素と CSS スタイルを表示および変更します。  
  
### JavaScript コンソール ウィンドウを使って WebView コントロールを検査およびデバッグします。  
  
1.  \(C\#、Visual Basic、C\+\+\) スクリプト デバッガーをアプリにアタッチします。  手順については最初のセクションを参照してください。  
  
2.  まだ行っていない場合はアプリに `WebView` コントロールを追加して、F5 を押すとデバッグが開始します。  
  
3.  **\[デバッグ\]**、**\[Windows\]**、**\[JavaScript コンソール\]** をクリックして、`WebView` コントロールの JavaScript コンソール ウィンドウを開きます。  
  
     JavaScript コンソール ウィンドウが開きます。  
  
4.  `Webview` コントロールが含まれるページに移動します。  
  
5.  コンソール ウィンドウで、Web ページ、または **\[ターゲット\]** リストの `WebView` コントロールに表示される `iFrame` を選択します。  
  
     ![JavaScript コンソール ウィンドウでのターゲット選択](~/docs/debugger/media/js_console_target.png "JS\_Console\_Target")  
  
    > [!NOTE]
    >  コンソールを使って、1 度に 1 つの `WebView`、`iFrame`、共有コントラクト、または Web ワーカーとやり取りできます。  各要素では、Web プラットフォーム ホストの個別のインスタンスが必要となります \(WWAHost.exe\)。  一度に 1 つのホストとやり取りできます。  
  
6.  [クイックスタート: JavaScript のデバッグ](../debugger/quickstart-debug-javascript-using-the-console.md)と[JavaScript コンソール コマンド](../debugger/javascript-console-commands.md)で説明されているように、アプリの変数を表示および変更するか、コンソール コマンドを使用します。  
  
## 参照  
 [クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)