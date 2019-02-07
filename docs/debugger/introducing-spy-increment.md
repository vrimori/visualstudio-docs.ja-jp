---
title: Spy++ の概要 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 371e707dae11dacbbcc9ec590e908cd66f6189ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027985"
---
# <a name="introducing-spy"></a>Spy++ の概要
Spy++ で実行できるタスクは以下のとおりです。  
  
- システム オブジェクト間の関係のグラフィカルなツリーを表示します。 これには、 [プロセス](../debugger/processes-view.md)、 [スレッド](../debugger/threads-view.md)、 [ウィンドウ](../debugger/windows-view.md)が含まれます。  
  
- 指定された [ウィンドウ](../debugger/how-to-search-for-a-window-in-windows-view.md)、 [スレッド](../debugger/how-to-search-for-a-thread-in-threads-view.md)、 [プロセス](../debugger/how-to-search-for-a-process-in-processes-view.md)、または [メッセージ](../debugger/how-to-search-for-a-message-in-messages-view.md)を検索します。  
  
- 選択された [ウィンドウ](../debugger/how-to-display-window-properties.md)、 [スレッド](../debugger/how-to-display-thread-properties.md)、 [プロセス](../debugger/how-to-display-process-properties.md)、または [メッセージ](../debugger/how-to-display-message-properties.md)のプロパティを表示します。  
  
- ビューでウィンドウ、スレッド、プロセス、またはメッセージを直接選択します。  
  
- [ファインダー ツール](../debugger/how-to-use-the-finder-tool.md) を使用して、マウス ポインターでウィンドウを選択します。  
  
- 設定[メッセージ オプション](../debugger/how-to-open-messages-view-from-find-window.md)複雑なメッセージ ログ選択パラメーターを使用しています。  
  
  Spy++ には、迅速な作業に役立つツールバーとハイパーリンクがあります。 また、アクティブなビューを更新する **[更新]** コマンド、スパイを容易にする **ウィンドウ ファインダー ツール** 、ビュー ウィンドウをカスタマイズする **[フォント]** ダイアログ ボックスが用意されています。 さらに、Spy++ ではユーザー設定の保存と復元が可能です。  
  
  さまざまな Spy++ ウィンドウでは、右クリックして頻繁に使用するコマンドのショートカット メニューを表示できます。 表示されるコマンドは、ポインターの位置によって異なります。 たとえば、ウィンドウ ビューのエントリを右クリックし、選択したウィンドウが表示されている場合は、ショートカット メニューの **[強調表示]** をクリックすると、選択したウィンドウの枠線が点滅して、より簡単に見つけられるようになります。  
  
> [!NOTE]
>  Spy++ に似たその他の 2 つのユーティリティがあります。PView は、プロセスとスレッド、およびあります詳細が表示されます。EXE、ダイナミック データ エクス チェンジ (DDE) メッセージを監視することができます。  
  
## <a name="64-bit-operating-systems"></a>64 ビット オペレーティング システム  
 Spy++ には 2 つのバージョンがあります。 1 番目のバージョンである Spy++ (spyxx.exe) は、32 ビット プロセスで実行しているウィンドウに送信されるメッセージを表示するように設計されています。 たとえば、Visual Studio は 32 ビット プロセスで実行されます。 したがって、Spy++ を使用して、 **ソリューション エクスプローラー**に送信されるメッセージを表示できます。 Spy++ の最初のバージョンで利用可能な 1 つは、Visual Studio でのほとんどのビルドの既定の構成では、32 ビット プロセスで実行するであるため、**ツール**Visual Studio でメニュー場合[必要なコンポーネントインストールされている](../debugger/how-to-start-spy-increment.md)します。 
  
 2 番目のバージョンである Spy++ (64 ビット) (spyxx_amd64.exe) は、64 ビット プロセスで実行しているウィンドウに送信されるメッセージを表示するように設計されています。 たとえば、64 ビットのオペレーティング システムでは、メモ帳は 64 ビット プロセスで実行されます。 したがって、Spy++ (64 ビット) を使用して、メモ帳に送信されるメッセージを表示できます。 通常、Spy++ (64 ビット) は、  
  
 ..\\*Visual Studio インストール フォルダー*\Common7\Tools\spyxx_amd64.exe.  
  
 どちらのバージョンの Spy++ も、コマンドラインから直接実行できます。  
  
> [!NOTE]
>  Spy++ (64 ビット) のファイル名には "amd" が含まれますが、すべての x64 Windows オペレーティング システムで動作します。  
  
## <a name="see-also"></a>関連項目 
 [方法: Spy++ の起動](../debugger/how-to-start-spy-increment.md)   
 [Spy++ の使用](../debugger/using-spy-increment.md)   
 [Spy++ ビュー](../debugger/spy-increment-views.md)   
 [Spy++ リファレンス](../debugger/spy-increment-reference.md)
