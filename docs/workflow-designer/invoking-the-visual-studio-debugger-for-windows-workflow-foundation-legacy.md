---
title: "Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "デバッガー, ワークフロー"
  - "ワークフローのデバッグ, デバッガーの開始"
  - "デバッグ, ワークフロー デバッガーの使用"
  - "ステップ イン コマンド"
  - "ステップ アウト コマンド"
  - "ステップ オーバー コマンド"
  - "ステップ実行"
  - "ステップ実行, コマンド"
  - "ワークフロー デバッガー, 開始"
  - "ワークフロー, デバッガー"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)
このトピックでは、従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]で [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションをデバッグするための [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーの使用方法について説明します。[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用します。  
  
 ほとんどの場合、他の Visual Studio プログラミング言語で書かれたプログラムをデバッグするときと同じようにして、従来のワークフローをデバッグすることができます。[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation を起動するには、次の方法に従います。  
  
-   **\[デバッグ\]** メニューの **\[プロセスにアタッチ\]** をクリックして、使用可能なプロセスの中から実行中のワークフロー インスタンスを選択します。  
  
-   **F5** キーを押して、ワークフローのインスタンスの実行を開始するか、ブレークポイントのヒット後に実行を続けます。  
  
## コードのステップ実行  
 このデバッガは、最も一般的なデバッグ手順の 1 つであるステップ実行 \(コードを 1 行ずつ段階的に実行していくこと\) をサポートします。コードをステップ実行するコマンドには、次の 3 つがあります。  
  
-   **ステップ イン**: **F11** キーを使ってアクティビティにステップ インできます。デバッガーは、任意の定義済みハンドラーにステップ インします。ハンドラーが定義されていない場合は、アクティビティをステップ オーバーするか、\(他のアクティビティを含む\) 複合アクティビティの場合には、実行される最初のアクティビティにステップ インします。**IfElseActivity**、**WhileActivity**、**ConditionedActivityGroup**、**ReplicatorActivity** の各アクティビティに関しては、デザイナからコード ハンドラへのステップ インはサポートされていません。これらのアクティビティに関連したハンドラをデバッグするには、明示的なブレークポイントをコード内に配置する必要があります。  
  
-   **ステップ アウト**: **Shift\-F11** キーを使ってアクティビティからステップ アウトできます。アクティビティからステップ アウトすると、現在のアクティビティとすべての兄弟アクティビティは最後まで実行されます。その後、デバッガーは現在のアクティビティの親で停止します。コード ハンドラーからステップ アウトするとき、デバッガーはハンドラーに関連付けられたアクティビティで停止します。  
  
-   **ステップ オーバー**: **F10** キーを使ってアクティビティをステップ オーバーできます。複合アクティビティをステップ オーバーするとき、デバッガーは複合アクティビティの最初の実行可能な子で停止します。複合ではないアクティビティ \(たとえば **CodeActivity** アクティビティ\) をステップ オーバーするとき、デバッガはそのアクティビティおよび関連するハンドラを実行して、次のアクティビティで停止します。実行されるアクティビティが複合アクティビティの最後の子アクティビティである場合には、デバッガはそれを実行した後、親アクティビティで停止します。  
  
## プロセスへのアタッチ  
 プロセスにアタッチすることによってワークフローをデバッグするには、**\[プロセスにアタッチ\]** ダイアログ ボックスの **\[選択可能なプロセス\]** リスト ボックスからプロセスを選択します。**\[自動: ワークフロー コード\]** が **\[アタッチ先\]** ボックスに表示されない場合は、**\[選択\]** をクリックします。**\[コードの種類の選択\]** ダイアログ ボックスの **\[次のコードの種類をデバッグする\]** をクリックして、**\[ワークフロー\]** を選択します。次に、**\[OK\]** をクリックして **\[アタッチ\]** をクリックします。  
  
## F5 キーを使ったデバッグ  
 たとえばワークフロー アクティビティ ライブラリを使用する際、ワークフロー ホスト アプリケーションとワークフロー DLL が別々の Visual Studio プロジェクトに配置されている場合には、**F5** キーを使ってワークフローをデバッグするためにはワークフロー DLL プロジェクトを Visual Studio ソリューション スタートアップ プロジェクトに設定する必要があります。さらに、ホスト アプリケーションのパスをワークフロー DLL プロジェクトの **\[外部プログラムの開始\]** プロパティに設定する必要もあります。  
  
 ソリューション エクスプローラーでスタートアップ プロジェクトを設定するには、プロジェクト名を右クリックして **\[スタートアップ プロジェクトに設定\]** をクリックします。ホストのパスを **\[外部プログラムの開始\]** プロパティに設定するには、ソリューション エクスプローラ内のワークフロー プロジェクトの **\[プロパティ\]** ノードをダブルクリックして、**\[デバッグ\]** タブをクリックします。**\[開始アクション\]** で **\[外部プログラムの開始\]** をクリックして、デバッグ対象のワークフローのホストである .exe ファイルのパスを入力します。  
  
 ホスト アプリケーションがスタートアップ プロジェクトとして設定されている場合は、Visual Studio デバッガだけがデバッグ用に起動されます。[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation は起動されません。Visual Studio デバッガを使用する場合、C\# または Visual Basic コード ブレークポイントだけがヒットします。ワークフロー デザイナで設定されたブレークポイントはヒットしません。たとえば、デザイナで <xref:System.Workflow.Activities.ParallelActivity> アクティビティに対して設定したブレークポイントは、[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation が使用される場合にヒットしますが、Visual Studio デバッガが使用される場合はヒットしません。  
  
## 参照  
 [方法: ワークフロー内にブレークポイントを設定する \(レガシ\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)