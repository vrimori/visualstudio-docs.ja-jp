---
title: "方法 : [モジュール] ウィンドウを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.modules"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッガー、[モジュール] ウィンドウ"
  - "[モジュール] ウィンドウ"
  - "実行可能ファイル、デバッグ中の表示"
  - "デバッグ [Visual Studio]、モジュールの表示"
  - "DLL、デバッグ中の表示"
  - "モジュール、表示"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : [モジュール] ウィンドウを使用する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  この機能は、SQL またはスクリプトのデバッグでは使用できません。  
  
 **\[モジュール\]** ウィンドウには、プログラムで使用される DLL と EXE の一覧と、それぞれの関連情報が表示されます。  
  
### \[モジュール\] ウィンドウを表示するには \(中断モードまたは実行モードの場合\)  
  
-   **\[デバッグ\]** メニューの **\[ウィンドウ\]** をポイントし、**\[モジュール\]** をクリックします。  
  
     既定では、**\[モジュール\]** ウィンドウには、モジュールが読み込み順に表示されます。  ただし、基準列を指定して並べ替えるように選択できます。  
  
### 基準列を指定して並べ替えるには  
  
-   列の上部にあるボタンをクリックします。  
  
     **\[モジュール\]** ウィンドウでは、ショートカット メニューを使用してシンボルを読み込んだり、シンボル パスを指定したりできます。  
  
## シンボルの読み込み  
 **\[モジュール\]** ウィンドウでは、デバッグ シンボルが読み込まれたモジュールを確認できます。  この情報は、**\[シンボルの状態\]** 列に表示されます。  **\[シンボルの読み込みをスキップしました\]**、**\[PDB ファイルを開けないか、ファイルが見つかりません\]**、または **\[含める\/除外する設定により、読み込みは無効になっています\]** と表示されている場合は、Microsoft のパブリック シンボル サーバーからシンボルをダウンロードするか、コンピューター上のシンボルのディレクトリからシンボルを読み込むことを指示できます。  詳細については、「[シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)」を参照してください。  
  
#### シンボルを手動で読み込むには  
  
1.  **\[モジュール\]** ウィンドウで、シンボルが読み込まれていないモジュールを右クリックします。  
  
2.  **\[シンボルの読み込み元\]** をポイントし、**\[Microsoft シンボル サーバー\]** または **\[シンボル パス\]** をクリックします。  
  
#### シンボル読み込みの設定を変更するには  
  
1.  **\[モジュール\]** ウィンドウで、任意のモジュールを右クリックします。  
  
2.  **\[シンボルの設定\]** をクリックします。  
  
     シンボルの読み込み設定を変更できます。詳細については「[シンボルの場所と読み込み動作を指定する](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)」を参照してください。  変更内容は、デバッグ セッションを再起動しないと有効になりません。  
  
#### 特定のモジュールのシンボル読み込み動作を変更するには  
  
1.  **\[モジュール\]** ウィンドウで、モジュールを右クリックします。  
  
2.  **\[自動シンボル読み込みの設定\]** をポイントし、**\[常に手動で読み込む\]** または **\[既定\]** をクリックします。  変更内容は、デバッグ セッションを再起動しないと有効になりません。  
  
## 参照  
 [Breaking Execution](http://msdn.microsoft.com/ja-jp/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)