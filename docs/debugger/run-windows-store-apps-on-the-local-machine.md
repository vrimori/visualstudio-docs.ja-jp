---
title: "ローカル コンピューターでの Windows ストア アプリの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ローカル コンピューターでの Windows ストア アプリの実行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Windows のみに適用されます](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Windows ストア アプリのパフォーマンス分析のデバッグ、テスト、実行を行う場合、Visual Studio をホストする同じコンピューター上でアプリを実行することができます。  デバイスのディスプレイがタッチ対応である場合は、アプリの全機能を実施できますが、そうでない場合の操作はマウスとキーボードに限定されます。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 以下を学習できます。  
  
 [ローカル コンピューター上での実行方法](#BKMK_How_to_run_on_a_local_machine)  
  
 [1 つのモニターで Windows ストア アプリと Visual Studio を切り替える方法](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> ローカル コンピューター上での実行方法  
 ローカル コンピューター上でアプリを実行するには、デバッガーの **\[標準\]** ツール バーの デバッグの開始ボタンの横にあるドロップダウン リストから **\[ローカル コンピューター\]** を選択します。  
  
 ![ローカル コンピューターでの実行](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
 **\[標準\]** ツールバーが表示されない場合は、**\[表示\]** メニューをクリックして **\[ツール バー\]** をポイントし、さらに **\[標準\]** をクリックします。  
  
 ドロップダウン リストでの選択はプロジェクトのプロパティ ファイルに残され、既定の実行ターゲットとなります。  
  
 実行ターゲットは、プロジェクトのプロパティ ファイルに直接設定することもできます。  **\[ソリューション エクスプローラー\]** でプロジェクト名を右クリックし、**\[プロパティ\]** をクリックします。  次に、以下のいずれかを実行します。  
  
-   C\# と Visual Basic のプロジェクトから、**\[デバッグ\]** をクリックして、次に **\[ターゲット デバイス\]** ドロップダウン リストから **\[ローカル コンピューター\]** を選択します。  
  
     ![C&#35; および Visual Basic プロジェクト プロパティ ページ](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN\_CS\_VB\_ProjProp\_Local")  
  
-   C\+\+ と JavaScript のプロジェクトから、**\[構成プロパティ\]** ノードを展開して **\[デバッグ\]** をクリックし、次に **\[起動するデバッガー\]** リストから **\[ローカル デバッガー\]** を選択します。  
  
     ![C&#43;&#43; および JavaScript プロジェクト プロパティ ページ](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN\_CPP\_JS\_ProjProp\_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> 1 つのモニターで Windows ストア アプリと Visual Studio を切り替える方法  
 **Windows ストア アプリの実行中のインスタンスから Visual Studio へ切り替えるには**  
  
 ローカル コンピューターで Windows ストア アプリを実行する際に 1 つのモニターだけを使用する場合は、アプリを実行したまま Visual Studio へ切り替えるといいでしょう。  たとえば、イベント待ちだったり長いループや無限ループにトラップされるなど、アプリがブレークポイントに到達できない状態にある可能性があります。  Visual Studio に戻るには、Alt \+ Tab キーを押します。