---
title: デバッガーでの Dll と実行可能ファイルの表示 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f582c435239c83503b179d6bb5e142936a41cb4b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279012"
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Dll と Visual Studio デバッガーで [モジュール] ウィンドウを使用して実行可能ファイルを表示します。
 
**モジュール**Dll と実行可能ファイル (EXE) は、プログラムによって使用され、それぞれの関連情報を表示するウィンドウが表示されます。 

> [!NOTE]
>  この機能は、SQL またはスクリプトのデバッグでは使用できません。 
  
### <a name="to-display-the-modules-window"></a>[モジュール] ウィンドウを表示するには  
  
-   をデバッグするときに選択します**デバッグ > Windows**し**モジュール**します。  
  
     既定で、**モジュール**ウィンドウは、読み込み順序でモジュールを並べ替えます。 ただし、基準列を指定して並べ替えるように選択できます。  
  
### <a name="to-sort-by-any-column"></a>基準列を指定して並べ替えるには  
  
-   列の上部にあるボタンをクリックします。  
  
     シンボルの読み込みまたはシンボル パスを指定することができます、**モジュール**ウィンドウ ショートカット メニューを使用します。  
  
## <a name="loading-symbols"></a>シンボルの読み込み  
 **モジュール**ウィンドウで、モジュールでは、デバッグ シンボルが読み込まれるを参照してください。 この情報が表示されます、**シンボルの状態**列。 済み状態の場合**Skipped loadingCannot が見つからないか、PDB ファイルを開く**、または**包含/除外の設定で無効にする読み込み**、Microsoft パブリック シンボルからシンボルをダウンロードするデバッガーに指示することができますサーバーまたはコンピューターにシンボルのディレクトリからシンボルを読み込みます。 詳細については、次を参照してください[指定シンボル (.pdb) とソース ファイル。](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>シンボルを手動で読み込むには  
  
1.  **モジュール**ウィンドウで、モジュールのシンボルが読み込まれていないを右クリックします。  
  
2.  をポイント**シンボルの読み込み元**し**Microsoft シンボル サーバー**または**シンボル パス**します。  
  
#### <a name="to-change-symbol-load-settings"></a>シンボル読み込みの設定を変更するには  
  
1.  **モジュール**ウィンドウで、任意のモジュールを右クリックします。  
  
2.  クリックして**シンボルの設定**します。  
  
     シンボルの読み込み設定を変更することができますようになりました[シンボルの場所を指定し、読み込み動作](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)します。 変更内容は、デバッグ セッションを再起動しないと有効になりません。  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>特定のモジュールのシンボル読み込み動作を変更するには  
  
1.  **モジュール**ウィンドウで、モジュールを右クリックします。  
  
2.  をポイント**自動シンボル読み込みの設定** をクリックし、**常に手動で読み込む**または**既定**します。 変更内容は、デバッグ セッションを再起動しないと有効になりません。  
  
## <a name="see-also"></a>関連項目  
 [実行の中断](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)