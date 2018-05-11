---
title: Visual Studio デバッガーでの呼び出し履歴の表示 |Microsoft ドキュメント
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d20a1ac9f1a09b93f577c6aa90f550ccd6ff0def
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>呼び出し履歴を表示して、呼び出し履歴 ウィンドウで、Visual Studio デバッガーを使用します。

使用して、**呼び出し履歴**ウィンドウで、関数またはプロシージャの呼び出しは、現在、スタック上を表示できます。 **呼び出し履歴** ウィンドウに表示するメソッドおよび関数が呼び出された順序。 呼び出し履歴を調査して、アプリの実行フローを理解することをお勧めします。
  
ときに[デバッグ シンボル](#bkmk_symbols)、呼び出し履歴の一部では使用できません、**呼び出し履歴**ウィンドウは、コール スタックの部分の正しい情報を表示できない可能性があります。 その場合は、次の表記が表示されます。  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> **呼び出し履歴**ウィンドウは Eclipse のようないくつかの Ide でデバッグ パースペクティブに似ています。 

> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ここで説明する内容と異なる場合があります。 設定を変更するには選択**インポートおよびエクスポート設定**上、**ツール**メニュー。  参照してください[IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>デバッガーで呼び出し履歴を表示します。 
  
-   デバッグ中に、**デバッグ**メニューの  **Windows > 呼び出し履歴**です。

 ![呼び出し履歴 ウィンドウ](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

黄色の矢印は、現在、実行ポインターが存在するスタック フレームを示します。 既定では、これは、スタック フレームの情報、ソースで**ローカル**、 **[自動変数]**、**ウォッチ**、および**逆アセンブル**windows. デバッガー コンテキストをスタック上の別のフレームに変更する場合は、行うことができますを[別のスタック フレームに切り替える](#bkmk_switch)です。   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>呼び出し履歴 ウィンドウでの非ユーザー コードを表示します。  
  
-   右クリックし、**呼び出し履歴**ウィンドウと選択**外部コードの表示**です。

非ユーザー コードに表示されていない場合にすべてのコードは、[マイ コードのみ](../debugger/just-my-code.md)を有効にします。 マネージ コードでは、非ユーザー コード フレームは既定で非表示します。 次の表記は、非ユーザー コード フレームの代わりに表示されます。  
  
**[\<外部コード >]**  
  
## <a name="bkmk_switch"></a> 別のスタック フレーム (デバッガーのコンテキストの変更) に切り替える
  
1.  **呼び出し履歴**ウィンドウで、スタック フレームのコードとデータを表示するを右クリックします。

    またはのフレームをダブルクリックすることができます、**呼び出し履歴**選択したフレームに切り替えるにはウィンドウです。 
  
2.  選択**フレームに切り替え**です。  
  
     巻いた尾の付いた緑色の矢印は、選択したスタック フレームの横に表示されます。 実行ポインターは、黄色の矢印でマークされた元のフレームに置かれたままです。 選択した場合**ステップ**または**続行**から、**デバッグ**] メニューの [元のフレームで実行が継続は、選択したフレームではなく、します。  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>呼び出し履歴上の関数のソース コードを表示します。  
  
-   **呼び出し履歴**ウィンドウで、ソース コードを表示する関数を右クリックしを参照してください**ソース コードへ移動**です。

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>呼び出し履歴 ウィンドウから特定の関数まで実行します。  
  
-  **呼び出し履歴**ウィンドウで、関数の選択を右クリックして**カーソルまで実行**です。  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>関数呼び出しの終了ポイントにブレークポイントを設定します。  
  
-   参照してください[呼び出し履歴の関数にブレークポイントを設定](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window)です。

## <a name="display-calls-to-or-from-another-thread"></a>別のスレッドから呼び出しを表示します。  
  
-   右クリックし、**呼び出し履歴**ウィンドウと選択**他のスレッドの呼び出しを含む**です。   
  
## <a name="visually-trace-the-call-stack"></a>呼び出し履歴を視覚的にトレースします。  

Visual Studio Enterprise (のみ) を使用している場合は、デバッグ中に呼び出し履歴コード マップを表示できます。

- **呼び出し履歴**ウィンドウで、ショートカット メニューを開きます。 選択**コード マップに呼び出し履歴を表示する**です。 (キーボード: **CTRL** + **SHIFT** + **`**)  
  
    詳細については、次を参照してください。[デバッグ中に、呼び出し履歴に対するメソッドのマップ](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)です。

![コード マップに呼び出し履歴を表示する](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>呼び出し履歴上の関数の逆アセンブリ コードを表示します。  
  
-   **呼び出し履歴**ウィンドウで、あるの逆アセンブリ コード関数を右クリックしを参照してください**アセンブルを**です。    

## <a name="change-the-optional-information-displayed"></a>表示される省略可能な情報を変更します。  
  
-   右クリックし、**呼び出し履歴**ウィンドウとセットまたはクリア**表示\<***情報***>**です。  
  
## <a name="bkmk_symbols"></a> モジュールのシンボルの読み込み
**呼び出し履歴**ウィンドウで、デバッグ シンボルが読み込まれたを現在持っていないコードのシンボルを読み込むことができます。 これらのシンボルには、Microsoft のパブリック シンボル サーバーからダウンロードされる .NET Framework シンボルやシステム シンボル、または、デバッグしているコンピューター上のシンボル パス内のシンボルを指定できます。  
  
参照してください[シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>シンボルを読み込むには  
  
1.  **呼び出し履歴**ウィンドウで、右クリックし、スタック フレームのどのシンボルが読み込まれていません。 フレームが淡色表示されます。  
  
2.  をポイント**シンボルの読み込み** をクリックし、 **Microsoft シンボル サーバー** (使用可能な場合) またはシンボル パスを参照します。  
  
### <a name="to-set-the-symbol-path"></a>シンボル パスを設定するには  
  
1.  **呼び出し履歴**ウィンドウで、選択**シンボル設定**ショートカット メニューからです。  
  
     **オプション**ダイアログ ボックスが表示され、**シンボル**ページが表示されます。  
  
2.  をクリックして**シンボル設定**です。  
  
3.  **オプション** ダイアログ ボックスで、フォルダー アイコンをクリックします。  
  
     **シンボル (.pdb) ファイルの場所**ボックス、カーソルが表示されます。  
  
4.  デバッグしているコンピューター上のシンボルの場所へのディレクトリ パス名を入力します。 ローカルおよびリモート デバッグは、これは、ローカル コンピューター上のパスです。
  
5.  **[OK]** をクリックして、**[オプション]** ダイアログ ボックスを閉じます。  
  
## <a name="see-also"></a>関連項目  
 [[呼び出し履歴] ウィンドウの混合コードと不足情報](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [ブレークポイントの使用](../debugger/using-breakpoints.md)