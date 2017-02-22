---
title: "方法 : DLL プロジェクトからデバッグする | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "デバッグ [Visual Studio], DLL"
  - "デバッグ (DLL を)"
  - "DLL プロジェクト, デバッグ"
  - "DLL, デバッグ (プロジェクトを)"
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : DLL プロジェクトからデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DLL プロジェクトのデバッグを開始するには、プロジェクトのプロパティで呼び出し元のアプリケーションを指定する必要があります。  C\+\+ のプロパティ ページは、C\# と Visual Basic のプロパティ ページとレイアウトおよび内容が異なります。  
  
 マネージ DLL がネイティブ コードによって呼び出され、両方をデバッグする場合は、このプロジェクトのプロパティで指定できます。  詳細については、「[方法 : 混合モードでデバッグする](../debugger/how-to-debug-in-mixed-mode.md)」を参照してください。  
  
> [!NOTE]
>  Visual Studio の Express Edition では、外部の呼び出し元アプリケーションを指定できません。  代わりに、実行可能なプロジェクトをソリューションに追加することが必要です。次に、これをスタートアップ プロジェクトとして設定し、実行可能なプロジェクトから DLL のメソッドを呼び出します。  
  
### C\+\+ プロジェクトで呼び出し元のアプリケーションを指定するには  
  
1.  **\[ソリューション エクスプローラ\]** でプロジェクト ノードを右クリックし、**\[プロパティ\]** をクリックします。  **\[デバッグ\]** タブに移動します。  
  
2.  ウィンドウの上部にある **\[構成\]** フィールドが **\[デバッグ\]** に設定されていることを確認します。  
  
3.  **\[構成プロパティ\/デバッグ\]** に移動します。  
  
4.  **\[起動するデバッガー\]** ボックスで、**\[ローカル Windows デバッガー\]** または **\[リモート Windows デバッガー\]** を選択します。  
  
5.  **\[コマンド\]** ボックスまたは **\[リモート コマンド\]** ボックスで、アプリケーションの完全修飾パス名を追加します。  
  
6.  **\[コマンド引数\]** ボックスに、必要なプログラム引数を追加します。  
  
### C\# または Visual Basic のプロジェクトで呼び出し元のアプリケーションを指定するには  
  
1.  **\[ソリューション エクスプローラ\]** でプロジェクト ノードを右クリックし、**\[プロパティ\]** をクリックします。  **\[デバッグ\]** タブに移動します。  
  
     **\[外部プログラムの開始\]** を選択し、実行するアプリケーションの完全修飾パス名を追加します。  
  
     外部プログラムのコマンド ライン引数を追加する必要がある場合、**\[コマンド ライン引数\]** フィールドで追加します。  
  
2.  URL としてアプリケーションを呼び出すこともできます。  ローカル ASP.NET アプリケーションが使用するマネージ DLL をデバッグする場合は、この手順を実行します。  
  
     **\[開始動作\]** の下の **\[ブラウザーを開始時に使用する URL\]** オプション ボタンをクリックし、URL を入力します。  
  
### DLL プロジェクトからデバッグを開始するには  
  
1.  必要に応じてブレークポイントを設定します。  
  
2.  デバッグを開始します \(F5 キー押すか、緑色の矢印をクリックするか、**\[デバッグ\/デバッグの開始\]** をクリック\)。  
  
## 参照  
 [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)   
 [C\# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)