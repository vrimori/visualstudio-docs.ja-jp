---
title: "ローカル コンピューター上の UWP アプリの実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08e0108a3fb7a93dc19fe1aa96988912068ace70
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>ローカル コンピューター上の UWP アプリを実行します。
![Windows にのみ適用されます](../debugger/media/windows_only_content.png "windows_only_content")  
  
 デバッグ、テスト、または、UWP アプリのパフォーマンス分析の実行、同じコンピューターにアプリの実行する Visual Studio をホストします。 デバイスのディスプレイがタッチ対応である場合は、アプリの全機能を実施できますが、そうでない場合の操作はマウスとキーボードに限定されます。  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>ローカル コンピューター上で実行する方法  
 アプリを実行する、ローカル コンピューターで、次のように選択します。**ローカル マシン**デバッガーのデバッグの開始ボタンの横にあるドロップダウン リストから**標準**ツールバー。  
  
 ![ローカル コンピューター上で実行](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 表示されない場合、**標準**ツールバーで、をクリックして、**ビュー**  メニューのをポイント**ツールバー**、順にクリック**標準**です。  
  
 ドロップダウン リストでの選択はプロジェクトのプロパティ ファイルに残され、既定の実行ターゲットとなります。  
  
 実行ターゲットは、プロジェクトのプロパティ ファイルに直接設定することもできます。 プロジェクト名を右クリックして**ソリューション エクスプ ローラー**を選択し**プロパティ**です。 次に、以下のいずれかを実行します。  
  
-   C# および Visual Basic のプロジェクトでクリックして**デバッグ**し、**ローカル マシン**から、**ターゲット デバイス**ドロップダウン リスト。  
  
     ![C &#35;です。Visual Basic プロジェクトのプロパティ ページ](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   C++ と JavaScript のプロジェクトで、展開、**構成プロパティ**ノード、をクリックして**デバッグ**、し、[**ローカル デバッガー**から、**デバッガー起動する**] ボックスの一覧です。  
  
     ![C &#43; #43 です。JavaScript プロジェクトのプロパティ ページおよび](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  