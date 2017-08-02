---
title: "Spy++ Toolbar | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++ toolbar"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spy++ Toolbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ツール バーは、Spy\+\+ のメニュー バーの下に表示されます。  ツール バーの表示と非表示を切り替えるには、**\[表示\]** メニューの **\[ツール バー\]** をクリックします。  
  
 ツール バーには次のコントロールがあります。  
  
## UIElement の一覧  
  
|ボタン|効果|  
|---------|--------|  
|![Spy&#43;&#43; の &#91;ウィンドウ&#93; ボタン](~/debugger/media/icon_spy--_windows.gif "Icon\_Spy\+\+\_Windows")|システム内にあるウィンドウとコントロールをツリー ビューで表示します。  詳細については、「[Windows View](../debugger/windows-view.md)」を参照してください。|  
|![Spy&#43;&#43; の &#91;プロセス&#93; ボタン](~/debugger/media/icon_spy--_processes.gif "Icon\_Spy\+\+\_Processes")|システム内にあるプロセスをツリー ビューで表示します。  詳細については、「[Processes View](../debugger/processes-view.md)」を参照してください。|  
|![Spy&#43;&#43; の &#91;スレッド&#93; ボタン](~/debugger/media/icon_spy--_threads.gif "Icon\_Spy\+\+\_Threads")|システム内にあるスレッドをツリー ビューで表示します。  詳細については、「[Threads View](../debugger/threads-view.md)」を参照してください。|  
|![Spy&#43;&#43; の &#91;メッセージ&#93; ボタン](~/debugger/media/icon_spy--_messages.gif "Icon\_Spy\+\+\_Messages")|ウィンドウ メッセージを表示するウィンドウが作成され、メッセージを表示するウィンドウの選択と、他のオプションの選択を行うための **\[メッセージ オプション\]** ダイアログ ボックスが表示されます。  詳細については、「[Messages View](../debugger/messages-view.md)」を参照してください。|  
|![Spy&#43;&#43; の &#91;ログの開始&#93; ボタン](~/debugger/media/icon_spy--_startlog.gif "Icon\_Spy\+\+\_StartLog")|メッセージのログ出力を開始し、メッセージ ストリームを表示します。  このコントロールは、**\[メッセージ\]** ウィンドウがアクティブ ウィンドウである場合にのみ使用できます。  詳細については、「[How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md)」を参照してください。|  
|![Spy&#43;&#43; の &#91;ログの終了&#93; ボタン](~/debugger/media/icon_spy--_stoplog.gif "Icon\_Spy\+\+\_StopLog")|メッセージのログ出力とメッセージ ストリームの表示を中止します。  このコントロールは、**\[メッセージ\]** ウィンドウがアクティブ ウィンドウである場合にのみ使用できます。  詳細については、「[How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md)」を参照してください。|  
|![Spy&#43;&#43; の &#91;ログのオプション&#93; ボタン](~/debugger/media/icon_spy--_logoptions.gif "Icon\_Spy\+\+\_LogOptions")|[&#91;メッセージ オプション&#93;](../debugger/message-options-dialog-box.md) ダイアログ ボックスを表示します。  このダイアログ ボックスを使用すると、表示するウィンドウとメッセージの種類を選択できます。  このコントロールは、**\[メッセージ\]** ウィンドウがアクティブ ウィンドウである場合にのみ使用できます。|  
|![Spy&#43;&#43; ログのクリア ボタン](~/debugger/media/spy--_clearlog.gif "Spy\+\+\_ClearLog")|アクティブな **\[メッセージ\]** ウィンドウの内容を消去します。  このコントロールは、**\[メッセージ\]** ウィンドウがアクティブ ウィンドウである場合にのみ使用できます。|  
|![Spy&#43;&#43; の &#91;ウィンドウ検索&#93; ボタン](~/debugger/media/icon_spy--_findwindow.gif "Icon\_Spy\+\+\_FindWindow")|[&#91;ウィンドウ検索&#93;](../debugger/find-window-dialog-box.md) ダイアログ ボックスを開きます。このダイアログ ボックスでは、ウィンドウの検索条件を設定し、プロパティまたはメッセージを表示できます。  詳細については、「[How to: Use the Finder Tool](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md)」を参照してください。|  
|![Spy&#43;&#43; の &#91;最初のウィンドウを検索&#93; ボタン](~/debugger/media/icon_spy--_window.gif "Icon\_Spy\+\+\_Window")|現在のビューで一致するウィンドウ、プロセス、スレッド、またはメッセージを検索します。|  
|![Spy&#43;&#43; の &#91;次のウィンドウを検索&#93; ボタン](~/debugger/media/icon_spy--_nextwindow.gif "Icon\_Spy\+\+\_NextWindow")|現在のビューで次に一致するウィンドウ、プロセス、スレッド、またはメッセージを検索します。  このコントロール \(および関連のメニュー コマンド\) は、一意でない有効な検索結果が存在する場合にのみ使用できます。  たとえば、ウィンドウ ツリーでウィンドウ ハンドルを検索条件として使用すると、ウィンドウ ツリー内でそのハンドルを持つウィンドウは 1 つしかないため一意の結果が返されます。この場合、**\[次を検索\]** は使用できません。|  
|![Spy&#43;&#43; の &#91;前のウィンドウを検索&#93; ボタン](~/debugger/media/icon_spy--_prevwindow.gif "Icon\_Spy\+\+\_PrevWindow")|現在のビューで前に一致するウィンドウ、プロセス、スレッド、またはメッセージを検索します。  このコントロール \(および関連のメニュー コマンド\) は、一意でない有効な検索結果が存在する場合にのみ使用できます。  たとえば、ウィンドウ ツリーでウィンドウ ハンドルを検索条件として使用すると、ウィンドウ ツリー内でそのハンドルを持つウィンドウは 1 つしかないため一意の結果が返されます。この場合、**\[前を検索\]** は使用できません。|  
|![Spy&#43;&#43; の &#91;プロパティ エクスプローラー&#93; ボタン](~/debugger/media/icon_spy--_propexp.gif "Icon\_Spy\+\+\_PropExp")|ウィンドウ ビューで選択されているウィンドウのプロパティを表示します。|  
|![Spy&#43;&#43; の &#91;最新の情報に更新&#93; ボタン](~/debugger/media/icon_spy--_refresh.gif "Icon\_Spy\+\+\_Refresh")|システム ビューを更新します。|  
  
## 参照  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)