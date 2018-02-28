---
title: "デバッガーで Dll と実行可能ファイルの表示 |Microsoft ドキュメント"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 772c252265e15c3c928fbcc47c756ceafd9e1362
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Dll および Visual Studio デバッガーの [モジュール] ウィンドウを使用して実行可能ファイルを表示します。
 
**モジュール**Dll と実行可能ファイル (EXE) は、プログラムで使用され、それぞれの関連情報を表示するウィンドウが表示されます。 

> [!NOTE]
>  この機能は、SQL またはスクリプトのデバッグでは使用できません。 
  
### <a name="to-display-the-modules-window"></a>[モジュール] ウィンドウを表示するには  
  
-   デバッグしている間は、選択**デバッグ > Windows**  をクリックし、**モジュール**です。  
  
     既定では、**モジュール**ウィンドウは、読み込み順でモジュールを並べ替えます。 ただし、基準列を指定して並べ替えるように選択できます。  
  
### <a name="to-sort-by-any-column"></a>基準列を指定して並べ替えるには  
  
-   列の上部にあるボタンをクリックします。  
  
     シンボルの読み込みまたはシンボル パスを指定することができます、**モジュール**ウィンドウ ショートカット メニューを使用します。  
  
## <a name="loading-symbols"></a>シンボルの読み込み  
 **モジュール**ウィンドウで、どのモジュールは、シンボルが読み込まれてをデバッグしておくことを確認できます。 この情報に表示されます、**シンボルの状態**列です。 表示されている場合**スキップ loadingCannot が見つからないか、PDB ファイルを開く**、または**読み込みを含める/除外の設定によって無効に**、Microsoft パブリック シンボルからシンボルをダウンロードするデバッガーを指示することができますサーバーまたはコンピューター上のシンボルのディレクトリからシンボルを読み込みます。 詳細については、次を参照してください[指定シンボル (.pdb) とソース ファイル。](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>シンボルを手動で読み込むには  
  
1.  **モジュール**ウィンドウで、モジュールのシンボルが読み込まれていないを右クリックします。  
  
2.  をポイント**シンボルの読み込み元** をクリックし、 **Microsoft シンボル サーバー**または**シンボル パス**です。  
  
#### <a name="to-change-symbol-load-settings"></a>シンボル読み込みの設定を変更するには  
  
1.  **モジュール**ウィンドウで、任意のモジュールを右クリックします。  
  
2.  をクリックして**シンボル設定**です。  
  
     シンボルの読み込みの設定を変更することが今すぐ[シンボルの場所を指定し、読み込み動作](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)です。 変更内容は、デバッグ セッションを再起動しないと有効になりません。  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>特定のモジュールのシンボル読み込み動作を変更するには  
  
1.  **モジュール** ウィンドウで、モジュールを右クリックします。  
  
2.  をポイント**自動シンボル読み込みの設定** をクリックし、**常に手動で読み込む**または**既定**です。 変更内容は、デバッグ セッションを再起動しないと有効になりません。  
  
## <a name="see-also"></a>参照  
 [実行の中断](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)