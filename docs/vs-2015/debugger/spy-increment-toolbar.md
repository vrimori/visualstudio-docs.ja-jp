---
title: Spy++ ツールバー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05dc7dd74af20c76a3b673d5960cd88331ad7d51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763326"
---
# <a name="spy-toolbar"></a>Spy++ ツール バー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spy++ のメニュー バーで、ツールバーが表示されます。 ツールバーを非表示、**ビュー**  メニューのをクリックして**ツールバー**します。  
  
 次のコントロールは、ツールバーの使用です。  
  
## <a name="uielement-list"></a>UIElement の一覧  
  
|ボタン|効果|  
|------------|------------|  
|![Spy&#43; &#43; Windows ボタン](../debugger/media/icon-spy-windows.gif "Icon_Spy + (_w)")|システム内のウィンドウとコントロールのツリー ビューを表示します。 詳細については、次を参照してください。 [Windows ビュー](../debugger/windows-view.md)します。|  
|![Spy&#43; &#43;ボタンの処理](../debugger/media/icon-spy-processes.gif "Icon_Spy + _Processes")|システムのプロセスのツリー ビューを表示します。 詳細については、次を参照してください。[プロセス ビュー](../debugger/processes-view.md)します。|  
|![Spy&#43; &#43;スレッド ボタン](../debugger/media/icon-spy-threads.gif "Icon_Spy + _Threads")|システム内のスレッドのツリー ビューを表示します。 詳細については、次を参照してください。[スレッド ビュー](../debugger/threads-view.md)します。|  
|![Spy&#43; &#43;メッセージ ボタン](../debugger/media/icon-spy-messages.gif "Icon_Spy + メッセージ (_m)")|ウィンドウ メッセージを表示するウィンドウを作成し、開きます、**メッセージ オプション** ダイアログ ボックスのメッセージが含まれるが表示され、その他のオプションも選択ウィンドウを選択するようにします。 詳細については、次を参照してください。[メッセージ ビュー](../debugger/messages-view.md)します。|  
|![Spy&#43; &#43;ログ ボタンをスタート](../debugger/media/icon-spy-startlog.gif "Icon_Spy + _StartLog")|メッセージのログ記録を開始し、メッセージ ストリームを表示します。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。 詳細については、次を参照してください。[方法: 開始とメッセージ ログの表示を停止](../debugger/how-to-start-and-stop-the-message-log-display.md)します。|  
|![Spy&#43; &#43;ログ ボタンを停止](../debugger/media/icon-spy-stoplog.gif "Icon_Spy + _StopLog")|メッセージ ログ出力とメッセージ ストリームの表示の停止です。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。 詳細については、次を参照してください。[方法: 開始とメッセージ ログの表示を停止](../debugger/how-to-start-and-stop-the-message-log-display.md)します。|  
|![Spy&#43; &#43;ログ オプション ボタン](../debugger/media/icon-spy-logoptions.gif "Icon_Spy + _LogOptions")|表示、[メッセージ オプション](../debugger/message-options-dialog-box.md) ダイアログ ボックス。 Windows を選択し、メッセージの種類を表示するには、このダイアログ ボックスを使用します。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。|  
|![Spy&#43; &#43;ログ ボタンをオフに](../debugger/media/spy-clearlog.gif "スパイ + _ClearLog")|アクティブな内容を消去**メッセージ**ウィンドウ。 このコントロールは、使用可能な場合にのみ、**メッセージ**ウィンドウはアクティブなウィンドウです。|  
|![Spy&#43; &#43;ウィンドウ ボタン](../debugger/media/icon-spy-findwindow.gif "Icon_Spy + _FindWindow")|開く、[ウィンドウ検索](../debugger/find-window-dialog-box.md) ダイアログ ボックスで、ウィンドウの検索条件を設定し、プロパティまたはメッセージを表示することができます。 詳細については、次を参照してください。[方法: ファインダー ツールを使用して、](../debugger/how-to-use-the-finder-tool.md)します。|  
|![Spy&#43; &#43;ウィンドウの最初のボタンを見つける](../debugger/media/icon-spy-window.gif "Icon_Spy + _Window")|一致するウィンドウをプロセス、スレッド、またはメッセージの現在のビューを検索します。|  
|![スパイ&#43;&#43;ウィンドウの [次へ] ボタンを見つける](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy:operator++ _NextWindow")|次の一致するウィンドウ、プロセス、スレッド、またはメッセージの現在のビューを検索します。 このコントロール (および関連メニュー コマンド) は一意でない有効な検索結果がある場合にのみ使用できます。 たとえば、ウィンドウ ハンドルを使用して、ウィンドウのツリーの検索条件としてが生成されます一意の結果をそのハンドルを持つウィンドウのツリーで 1 つのウィンドウがあるため、このインスタンスで**次を検索**は使用できません。|  
|![Spy&#43; &#43;前のウィンドウ ボタン](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy + _PrevWindow")|前の一致するウィンドウ、プロセス、スレッド、またはメッセージの現在のビューを検索します。 このコントロール (および関連メニュー コマンド) は一意でない有効な検索結果がある場合にのみ使用できます。 たとえば、ウィンドウ ハンドルを使用して、ウィンドウのツリーの検索条件としてが生成されます一意の結果をそのハンドルを持つウィンドウのツリーで 1 つのウィンドウがあるため、このインスタンスで**前を検索**は使用できません。|  
|![Spy&#43; &#43;プロパティ エクスプ ローラー ボタン](../debugger/media/icon-spy-propexp.gif "Icon_Spy + _PropExp")|Windows のビューで選択されているウィンドウのプロパティを表示します。|  
|![Spy&#43; &#43;更新ボタン](../debugger/media/icon-spy-refresh.gif "Icon_Spy + 更新 (_r)")|システム ビューを更新します。|  
  
## <a name="see-also"></a>関連項目  
 [Spy++ の使用](../debugger/using-spy-increment.md)   
 [Spy++ ビュー](../debugger/spy-increment-views.md)   
 [Spy++ リファレンス](../debugger/spy-increment-reference.md)



