---
title: Dll と実行可能ファイルを表示します。
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd628869d8a642cc6debad726f6c82df71a3b1ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014030"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>[モジュール] ウィンドウで、Dll と実行可能ファイルを表示 (C#、C++、Visual Basic、 F#)
 
Visual Studio がデバッグ中に、**モジュール** ウィンドウの一覧し、Dll と実行可能ファイルに関する情報が表示されます (*.exe*ファイル)、アプリで使用します。 

> [!NOTE]
> [モジュール] ウィンドウでは、SQL またはスクリプトのデバッグに使用できません。 
  
## <a name="use-the-modules-window"></a>[モジュール] ウィンドウを使用する

デバッグ中にモジュール ウィンドウを開き、選択**デバッグ** > **Windows** > **モジュール**(またはキーを押します**Ctrl + Alt + U**). 
  
既定では、**[モジュール]** ウィンドウには、モジュールが読み込み順に表示されます。 ウィンドウの任意の列を並べ替えるには、列の上部にあるヘッダーを選択します。  
  
## <a name="load-symbols"></a>シンボルの読み込み  

**シンボルの状態**内の列、**モジュール**モジュールでは、デバッグ シンボルが読み込まれるウィンドウに表示されます。 状態の場合**シンボルの読み込みをスキップ**、**見つからないか、PDB ファイルを開くことはできません**、または**包含/除外の設定で無効にする読み込み**シンボルを手動で読み込むことができます。 詳細については、シンボルの読み込みとは、次を参照してください。[シンボル (.pdb) ファイルとソース ファイルを指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)します。

**シンボルを手動で読み込むには:**  

1. **モジュール**ウィンドウで、右クリック、モジュールのシンボルが読み込まれていません。 
   
   - 選択**シンボル読み込み情報**理由の詳細については、シンボルが読み込まれませんでした。 
   
   - 選択**シンボルの読み込み**手動でシンボルを読み込めません。  
   
1. シンボルが読み込まれない場合は、選択**シンボルの設定**を開く、**オプション**ダイアログ ボックスで、指定するか、シンボルの読み込み場所を変更します。 
   
   パブリックの Microsoft シンボル サーバーまたは他のサーバーからシンボルをダウンロードまたはフォルダーからコンピューターにシンボルを読み込むことができます。 詳細については、次を参照してください。[シンボルの場所を指定し、読み込み動作](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)します。   

**シンボルの読み込み動作の設定を変更するには。**  

1. **[モジュール]** ウィンドウで、任意のモジュールを右クリックします。  
   
1. 選択**シンボルの設定**します。  
  
1. 選択**すべてのシンボルを読み込む**、またはを含めるか除外するモジュールを選択します。  
  
1. **[OK]** を選択します。 変更は、次のデバッグ セッションで反映されます。  
  
**シンボルの読み込みモジュールの特定の動作を変更するには。**  

1.  **[モジュール]** ウィンドウで、モジュールを右クリックします。  

1.  右クリック メニューで選択または選択解除**常にロード自動的**します。 変更は、次のデバッグ セッションで反映されます。  
  
## <a name="see-also"></a>関連項目  
 [実行の中断](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)   
 [シンボル (.pdb) とソース ファイルの指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)