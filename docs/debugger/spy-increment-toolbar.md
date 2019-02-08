---
title: Spy++ ツールバー |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7a3213d614caa19fb6df77a72efd05e36484c77
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982677"
---
# <a name="spy-toolbar"></a>Spy++ ツール バー
Spy++ のメニュー バーで、ツールバーが表示されます。 ツールバーを非表示、**ビュー**  メニューのをクリックして**ツールバー**します。  
  
 次のコントロールは、ツールバーの使用です。  
  
## <a name="uielement-list"></a>UIElement の一覧  
  
|ボタン|効果|  
|------------|------------|  
|![Spy&#43; &#43; Windows ボタン](../debugger/media/icon_spy--_windows.gif "Icon_Spy + (_w)")|システム内のウィンドウとコントロールのツリー ビューを表示します。 詳細については、次を参照してください。 [Windows ビュー](../debugger/windows-view.md)します。|  
|![Spy&#43; &#43;ボタンの処理](../debugger/media/icon_spy--_processes.gif "Icon_Spy + _Processes")|システムのプロセスのツリー ビューを表示します。 詳細については、次を参照してください。[プロセス ビュー](../debugger/processes-view.md)します。|  
|![Spy&#43; &#43;スレッド ボタン](../debugger/media/icon_spy--_threads.gif "Icon_Spy + _Threads")|システム内のスレッドのツリー ビューを表示します。 詳細については、次を参照してください。[スレッド ビュー](../debugger/threads-view.md)します。|  
|![Spy&#43; &#43;メッセージ ボタン](../debugger/media/icon_spy--_messages.gif "Icon_Spy + メッセージ (_m)")|ウィンドウ メッセージを表示するウィンドウを作成し、開きます、**メッセージ オプション** ダイアログ ボックスのメッセージが含まれるが表示され、その他のオプションも選択ウィンドウを選択するようにします。 詳細については、次を参照してください。[メッセージ ビュー](../debugger/messages-view.md)します。|  
|![Spy&#43; &#43;ログ ボタンをスタート](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + _StartLog")|メッセージのログ記録を開始し、メッセージ ストリームを表示します。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。 詳細については、「[方法 :メッセージ ログの表示を開始および終了する](../debugger/how-to-start-and-stop-the-message-log-display.md)」を参照してください。|  
|![Spy&#43; &#43;ログ ボタンを停止](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + _StopLog")|メッセージ ログ出力とメッセージ ストリームの表示の停止です。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。 詳細については、「[方法 :メッセージ ログの表示を開始および終了する](../debugger/how-to-start-and-stop-the-message-log-display.md)」を参照してください。|  
|![Spy&#43; &#43;ログ オプション ボタン](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + _LogOptions")|表示、[メッセージ オプション](../debugger/message-options-dialog-box.md) ダイアログ ボックス。 Windows を選択し、メッセージの種類を表示するには、このダイアログ ボックスを使用します。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。|  
|![Spy&#43; &#43;ログ ボタンをオフに](../debugger/media/spy--_clearlog.gif "スパイ + _ClearLog")|アクティブな内容を消去**メッセージ**ウィンドウ。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。|  
|![Spy&#43; &#43;ウィンドウ ボタン](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + _FindWindow")|開く、[ウィンドウ検索](../debugger/find-window-dialog-box.md) ダイアログ ボックスで、ウィンドウの検索条件を設定し、プロパティまたはメッセージを表示することができます。 詳細については、「[方法 :ファインダー ツールを使用する](../debugger/how-to-use-the-finder-tool.md)」を参照してください。|  
|![Spy&#43; &#43;ウィンドウの最初のボタンを見つける](../debugger/media/icon_spy--_window.gif "Icon_Spy + _Window")|一致するウィンドウをプロセス、スレッド、またはメッセージの現在のビューを検索します。|  
|![Spy&#43; &#43;ウィンドウの [次へ] ボタンを見つける](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + _NextWindow")|次の一致するウィンドウ、プロセス、スレッド、またはメッセージの現在のビューを検索します。 このコントロール (および関連メニュー コマンド) は一意でない有効な検索結果がある場合にのみ使用できます。 たとえば、ウィンドウ ハンドルを使用して、ウィンドウのツリーの検索条件としてが生成されます一意の結果をそのハンドルを持つウィンドウのツリーで 1 つのウィンドウがあるため、このインスタンスで**次を検索**は使用できません。|  
|![Spy&#43; &#43;前のウィンドウ ボタン](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + _PrevWindow")|前の一致するウィンドウ、プロセス、スレッド、またはメッセージの現在のビューを検索します。 このコントロール (および関連メニュー コマンド) は一意でない有効な検索結果がある場合にのみ使用できます。 たとえば、ウィンドウ ハンドルを使用して、ウィンドウのツリーの検索条件としてが生成されます一意の結果をそのハンドルを持つウィンドウのツリーで 1 つのウィンドウがあるため、このインスタンスで**前を検索**は使用できません。|  
|![Spy&#43; &#43;プロパティ エクスプ ローラー ボタン](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + _PropExp")|Windows のビューで選択されているウィンドウのプロパティを表示します。|  
|![Spy&#43; &#43;更新ボタン](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + 更新 (_r)")|システム ビューを更新します。|  
  
## <a name="see-also"></a>関連項目
 [Spy++ の使用](../debugger/using-spy-increment.md)   
 [Spy++ ビュー](../debugger/spy-increment-views.md)   
 [Spy++ リファレンス](../debugger/spy-increment-reference.md)
