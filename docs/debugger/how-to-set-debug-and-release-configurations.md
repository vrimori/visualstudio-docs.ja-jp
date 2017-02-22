---
title: "方法 : デバッグ構成とリリース構成を設定する | Microsoft Docs"
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
  - "vs.debug.builds"
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
  - "ビルド構成, デバッグ"
  - "ビルド構成, リリース"
  - "構成, リリース"
  - "デバッグ ビルド"
  - "デバッグ ビルド, 変更 (構成設定の)"
  - "デバッグ ビルド, 切り替え (リリース ビルドへの)"
  - "デバッグ構成"
  - "デバッグ [Visual Studio], デバッグ構成"
  - "デバッグ [Visual Studio], リリース構成"
  - "プロジェクト [Visual Studio], デバッグ構成"
  - "プロジェクト [Visual Studio], リリース構成"
  - "リリース ビルド, 変更 (設定を)"
  - "リリース ビルド, 切り替え (デバッグ ビルドへの)"
  - "Visual Basic プロジェクト, デバッグ ビルドとリリース ビルド"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : デバッグ構成とリリース構成を設定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio プロジェクトでは、ご使用のプログラムに対応するリリースとデバッグ構成を個別に用意しています。  名前が示すように、デバッグ バージョンはデバッグ用、リリース バージョンは最終リリース配布用のビルドです。  
  
 プログラムのデバッグ構成のコンパイルでは、シンボリック デバッグ情報が完全に含まれ、最適化は行われません。  ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。  
  
 プログラムのリリース構成は、シンボリック デバッグ情報を含まず、完全に最適化されます。  使用しているコンパイラ オプションによっては、デバッグ情報が PDB ファイル内に生成される場合があります。  PDB ファイルを作成すると、後でリリース バージョンをデバッグする際に大きく役立つことがあります。  
  
 ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
 ビルド構成は、**\[ビルド\]** メニュー、ツールバー、またはプロジェクトのプロパティ ページを使用して変更できます。  プロジェクト プロパティ ページは、言語固有のページです。  次の手順では、メニューとツールバーからビルド構成を変更する方法を示します。  各種言語のプロジェクトでビルド構成を変更する方法の詳細については、以下の「関連項目」を参照してください。  
  
### ビルド構成を変更するには  
  
1.  \[ビルド\] メニューからの変更: **\[ビルド\] \/ \[構成マネージャー\]** の順にクリックし、**\[デバッグ\]** または **\[リリース\]** を選択します。  
  
2.  ツールバーの場合は、**\[ソリューション構成\]** リスト ボックスから **\[デバッグ\]** または **\[リリース\]** をクリックします。  
  
     ![ツール バーのビルド構成](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     このツールバーは、Express Edition では使用できません。  構成を選択するために **\[ソリューションのビルド\] \(F6\)** と **\[デバッグの開始\] \(F5\)** のメニュー項目を使用できます。  
  
## 参照  
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C\# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)