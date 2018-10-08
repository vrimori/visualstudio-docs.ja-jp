---
title: WebView コントロールのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6b75f9dadbe1223c41989ff148028a355157bff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539055"
---
# <a name="debug-a-webview-control"></a>WebView コントロールのデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[WebView コントロールのデバッグ](https://docs.microsoft.com/visualstudio/debugger/debug-a-webview-control)します。  
  
Windows および Windows Phone に適用されます] (../Image/windows_and_phone_content.png"windows_and_phone_content")  
  
 Windows Runtime アプリで `WebView` コントロールを検査しデバッグするには、アプリの開始時にスクリプト デバッガーをアタッチするよう Visual Studio を設定できます。 Visual Studio 2013 Update 2 から、デバッガーを使用して `WebView` コントロールと 2 つの方法で対話できます。  
  
-   開く、 [DOM Explorer](../debugger/quickstart-debug-html-and-css.md)の`WebView`インスタンス、DOM 要素を検査し、CSS スタイルの問題を調査、およびスタイルに対する動的な変更をテストします。  
  
-   Web ページを選択または`iFrame`に表示される、`WebView`でターゲットとしてのインスタンス、 [JavaScript コンソール](../debugger/javascript-console-commands.md)ウィンドウで、コンソールのコマンドを使用して web ページと対話し、します。 コンソールは、現在のスクリプト実行コンテキストへのアクセスを提供します。  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>デバッガーのアタッチ (C#、Visual Basic、C++)  
  
1.  Visual Studio で、Windows Runtime アプリに `WebView` コントロールを追加します。  
  
2.  ソリューション エクスプ ローラーでプロジェクトのプロパティを選択して開きます**プロパティ**プロジェクトのショートカット メニューから。  
  
3.  選択**デバッグ**します。 **アプリケーション プロセス**一覧で、選択**スクリプト**します。  
  
     ![スクリプト デバッガーをアタッチ](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (省略可能)Visual Studio の Express 以外のバージョン、・ イン タイム (JIT) デバッグを無効にする**ツール**、**オプション**、**デバッグ**、**ジャストイン タイム**、スクリプトのデバッグし、JIT を無効にするとします。  
  
    > [!NOTE]
    >  JIT デバッグを無効にすると、一部の Web ページで生じる未処理の例外のダイアログ ボックスを非表示にできます。 Visual Studio Express では、JIT デバッグは常に無効となっています。  
  
5.  F5 キーを押してデバッグを開始します。  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>DOM Explorer を使って WebView コントロールを検査およびデバッグします。  
  
1.  (C#、Visual Basic、C++) スクリプト デバッガーをアプリにアタッチします。 手順については最初のセクションを参照してください。  
  
2.  まだ行っていない場合はアプリに `WebView` コントロールを追加して、F5 を押すとデバッグが開始します。  
  
3.  `Webview` コントロールが含まれるページに移動します。  
  
4.  DOM Explorer ウィンドウを開き、`WebView`コントロールを選択して**デバッグ**、 **Windows**、 **DOM Explorer**の URL を選択し、`WebView`しました。検査するとしてください。  
  
     ![DOM Explorer を開く](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     `WebView` に関連付けられた DOM Explorer が Visual Studio の新しいタブとして表示されます。  
  
5.  説明に従って、ライブ DOM 要素と CSS スタイルの変更を表示および[DOM Explorer を使用してデバッグの CSS スタイル](../debugger/debug-css-styles-using-dom-explorer.md)します。  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>JavaScript コンソール ウィンドウを使って WebView コントロールを検査およびデバッグします。  
  
1.  (C#、Visual Basic、C++) スクリプト デバッガーをアプリにアタッチします。 手順については最初のセクションを参照してください。  
  
2.  まだ行っていない場合はアプリに `WebView` コントロールを追加して、F5 を押すとデバッグが開始します。  
  
3.  JavaScript コンソール ウィンドウを開き、`WebView`コントロールを選択して**デバッグ**、 **Windows**、 **JavaScript コンソール**します。  
  
     JavaScript コンソール ウィンドウが開きます。  
  
4.  `Webview` コントロールが含まれるページに移動します。  
  
5.  コンソール ウィンドウで、web ページを選択します。 または、`iFrame`によって表示される、`WebView`を制御、**ターゲット**一覧。  
  
     ![JavaScript コンソール ウィンドウでの選択の対象](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  コンソールを使って、1 度に 1 つの `WebView`、`iFrame`、共有コントラクト、または Web ワーカーとやり取りできます。 各要素では、Web プラットフォーム ホストの個別のインスタンスが必要となります (WWAHost.exe)。 一度に 1 つのホストとやり取りできます。  
  
6.  表示し、アプリでの変数を変更または」の説明に従って、コンソールのコマンドを使用して[クイック スタート: JavaScript のデバッグ](../debugger/quickstart-debug-javascript-using-the-console.md)と[JavaScript Console commands](../debugger/javascript-console-commands.md)します。  
  
## <a name="see-also"></a>関連項目  
 [クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)



