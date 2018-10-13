---
title: Windows ストア アプリの実行、ローカル コンピューターの |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b460d1eecfe96cddce27926ee8e31aae258d8dcf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188386"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>ローカル コンピューターでの Windows ストア アプリの実行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows にのみ適用されます] (../Image/windows_only_content.png"windows_only_content")  
  
 Windows ストア アプリのパフォーマンス分析のデバッグ、テスト、実行を行う場合、Visual Studio をホストする同じコンピューター上でアプリを実行することができます。 デバイスのディスプレイがタッチ対応である場合は、アプリの全機能を実施できますが、そうでない場合の操作はマウスとキーボードに限定されます。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 以下を学習できます。  
  
 [ローカル コンピューターで実行する方法](#BKMK_How_to_run_on_a_local_machine)  
  
 [Windows ストア アプリと Visual Studio の間で 1 つのモニターを有効にする方法](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> ローカル コンピューターで実行する方法  
 アプリをローカル コンピューターで実行する次のように選択します。**ローカル マシン**デバッガーの [デバッグ開始] ボタンの横にあるドロップダウン リストから**標準**ツールバー。  
  
 ![ローカル コンピューターで実行](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 表示されない場合、**標準**ツールバーで、をクリックして、**ビュー**メニューで、**ツールバー**、順にクリックします**標準**します。  
  
 ドロップダウン リストでの選択はプロジェクトのプロパティ ファイルに残され、既定の実行ターゲットとなります。  
  
 実行ターゲットは、プロジェクトのプロパティ ファイルに直接設定することもできます。 プロジェクト名を右クリックして**ソリューション エクスプ ローラー**選び、**プロパティ**します。 次に、以下のいずれかを実行します。  
  
-   C# および Visual Basic のプロジェクトで次のようにクリックします。**デバッグ**選び**ローカル マシン**から、**ターゲット デバイス**ドロップダウン リスト。  
  
     ![C&#35;と Visual Basic プロジェクトのプロパティ ページ](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   C++ と JavaScript のプロジェクトで、展開、**構成プロパティ**ノード、をクリックして**デバッグ**、し、**ローカル デバッガー**から、**デバッガー起動する**一覧。  
  
     ![C&#43; &#43;および JavaScript プロジェクト プロパティ ページ](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Windows ストア アプリと Visual Studio の間で 1 つのモニターを有効にする方法  
 **Windows ストア アプリの実行中のインスタンスから Visual Studio に切り替え**  
  
 ローカル コンピューターで Windows ストア アプリを実行する際に 1 つのモニターだけを使用する場合は、アプリを実行したまま Visual Studio へ切り替えるといいでしょう。 たとえば、イベント待ちだったり長いループや無限ループにトラップされるなど、アプリがブレークポイントに到達できない状態にある可能性があります。 Visual Studio に戻るには、Alt + Tab キーを押します。



