---
title: '方法: [呼び出し履歴] ウィンドウを使用して、|Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 45
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75b617e9de62c20cc1e8a32cf993f5f03201f4fc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592727"
---
# <a name="how-to-use-the-call-stack-window"></a>方法 : [呼び出し履歴] ウィンドウを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio のデバッガーで呼び出し履歴を表示](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-call-stack-window)します。  
  
使用して、**呼び出し履歴**ウィンドウで、現在、スタック上にある関数またはプロシージャの呼び出しを表示できます。  
  
 **呼び出し履歴**ウィンドウには、各関数とで記述されているプログラミング言語の名前が表示されます。 関数またはプロシージャ名に、モジュール名、行番号、パラメーター名、型、値などのオプション情報が追加される場合があります。 このオプション情報の表示は、オンとオフを切り替えることができます。  
  
 黄色の矢印は、現在、実行ポインターが存在するスタック フレームを示します。 既定では、これは、ソース内の情報が表示されます、フレーム**逆アセンブル**、**ローカル**、**ウォッチ**、および **[自動変数]** windows。 スタック上の別のフレームにコンテキストを変更する場合は、行うことができますを、**呼び出し履歴**ウィンドウ。  
  
 デバッグ シンボルが、コール スタックの一部で使用できない場合、**呼び出し履歴**ウィンドウでコール スタックの部分の正しい情報を表示できない可能性があります。 次のような出力が表示されます。  
  
 [下のフレームは間違っているか、または見つかりません。name.dll に対して読み込まれたシンボルはありません。]  
  
 既定ではマネージ コード。 **呼び出し履歴**ウィンドウが非ユーザー コードに関する情報を非表示にします。 非表示情報の代わりに次のような出力が表示されます。  
  
 **[\<外部コード >]**  
  
 非ユーザー コードとは "マイ コード" 以外のすべてのコードです。ショートカット メニューを使用して非ユーザー コードの呼び出し履歴情報を表示することもできます。  
  
 ショートカット メニューを使用することにより、スレッド間の呼び出しを表示するかどうかを選択できます。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。 設定を変更するには、次のように選択します。**インポートおよびエクスポート設定**上、**ツール**メニュー。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>[呼び出し履歴] ウィンドウを表示するには (中断モードまたは実行モードの場合)  
  
-   **デバッグ**メニューの **[Windows]** をクリックし、**呼び出し履歴**します。  
  
### <a name="to-change-the-optional-information-displayed"></a>表示されるオプション情報を変更するには  
  
-   右クリックし、**呼び出し履歴**ウィンドウとセットまたはクリア**表示\<** _情報_**>**.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>[呼び出し履歴] ウィンドウで非ユーザー コードのフレームを表示するには  
  
-   右クリックし、**呼び出し履歴**ウィンドウと選択**外部コードの表示**します。  
  
### <a name="to-switch-to-another-stack-frame"></a>別のスタック フレームに切り替えるには  
  
1.  **呼び出し履歴**ウィンドウ フレームを右クリックしてのコードやデータを表示するがあります。  
  
2.  選択**フレームに切り替え**します。  
  
     巻いた尾の付いた緑色の矢印が、選択したフレームの横に表示されます。 実行ポインターは、黄色の矢印でマークされた元のフレームに置かれたままです。 選択した場合**手順**または**続行**から、**デバッグ**] メニューの [元のフレームで実行が継続は、選択したフレームではなく、します。  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>別のスレッドとの間の呼び出しを表示するには  
  
-   右クリックし、**呼び出し履歴**ウィンドウと選択**他のスレッドの呼び出しを含む**します。  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>呼び出し履歴上の関数のソース コードを表示するには  
  
-   **呼び出し履歴**ウィンドウで、右クリックを表示して選択する関数のソース コードを表示**ソース コードへ移動**します。  
  
### <a name="to-visually-trace-the-call-stack"></a>呼び出し履歴を視覚的にトレースするには  
  
1.  **呼び出し履歴**ウィンドウで、ショートカット メニューを開きます。 選択**コード マップに呼び出し履歴を表示**します。 (キーボード: **CTRL** + **SHIFT** + **`**)  
  
     参照してください[デバッグ中に呼び出し履歴に対するメソッドのマップ](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)します。  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>呼び出し履歴上の関数の逆アセンブリ コードを表示するには  
  
-   **呼び出し履歴**ウィンドウで、右クリックして選択する、逆アセンブリ コードを関数**アセンブルを**します。  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>[呼び出し履歴] ウィンドウで特定の関数までを実行するには  
  
-  **呼び出し履歴**ウィンドウで、関数の選択を右クリックして**カーソルまで実行**します。  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>関数呼び出しの終了ポイントにブレークポイントを設定するには  
  
-   参照してください[呼び出し履歴の関数にブレークポイントを設定](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window)します。  
  
### <a name="to-load-symbols-for-a-module"></a>モジュールのシンボルを読み込むには  
  
-   **呼び出し履歴**ウィンドウで、モジュールのシンボルを表示するフレームを右クリックを再読み込みを選択する**シンボルの読み込み**します。  
  
## <a name="loading-symbols"></a>シンボルの読み込み  
 **呼び出し履歴**ウィンドウで、デバッグ シンボルが読み込まれていないコードのシンボルを読み込むことができます。 これらのシンボルには、Microsoft のパブリック シンボル サーバーからダウンロードされる .NET Framework シンボルやシステム シンボル、または、デバッグしているコンピューター上のシンボル パス内のシンボルを指定できます。  
  
 参照してください[シンボル (.pdb) を指定し、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>シンボルを読み込むには  
  
1.  **呼び出し履歴**ウィンドウで、右クリック、フレームのどのシンボルが読み込まれていません。 フレームが淡色表示されます。  
  
2.  をポイント**シンボルの読み込み元**し**Microsoft シンボル サーバー**または**シンボル パス**します。  
  
#### <a name="to-set-the-symbol-path"></a>シンボル パスを設定するには  
  
1.  **呼び出し履歴**ウィンドウで、選択**シンボル設定**ショートカット メニューから。  
  
     **オプション** ダイアログ ボックスが表示されます、**シンボル**ページが表示されます。  
  
2.  クリックして**シンボルの設定**します。  
  
3.  **オプション** ダイアログ ボックスで、フォルダー アイコンをクリックします。  
  
     **シンボル (.pdb) ファイルの場所**ボックス、カーソルが表示されます。  
  
4.  デバッグしているコンピューター上のシンボルの場所へのディレクトリ パス名を入力します。 ローカル デバッグの場合、これはローカル コンピューターです。 リモート デバッグの場合、これはリモート コンピューターです。  
  
5.  **[OK]** をクリックして、**[オプション]** ダイアログ ボックスを閉じます。  
  
## <a name="see-also"></a>関連項目  
 [混合コードと不足情報、呼び出し履歴 ウィンドウ](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [方法: Windows のデバッガーの数値書式の変更](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [シンボル (.pdb) を指定し、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [ブレークポイントの使用](../debugger/using-breakpoints.md)





