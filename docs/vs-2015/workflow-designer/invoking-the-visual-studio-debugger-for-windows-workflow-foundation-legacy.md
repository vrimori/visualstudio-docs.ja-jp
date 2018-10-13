---
title: Visual Studio Debugger for Windows Workflow Foundation (レガシ) の起動 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f5fd785de6db5bb951088e56fe13a6d63650bf92
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306099"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)
このトピックでは、従来の [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]で [!INCLUDE[wf](../includes/wf-md.md)] アプリケーションをデバッグするための [!INCLUDE[wfd1](../includes/wfd1-md.md)] デバッガーの使用方法について説明します。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用します。  
  
 ほとんどの場合、他の Visual Studio プログラミング言語で書かれたプログラムをデバッグするときと同じようにして、従来のワークフローをデバッグすることができます。 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation を起動するには、次の方法に従います。  
  
-   選択**プロセスにアタッチ**で、**デバッグ**を可能なプロセスからワークフロー インスタンスの実行を選択します。  
  
-   キーを押して**F5**ワークフローのインスタンスの実行を開始するか、ブレークポイントにヒットした後に実行を続けます。  
  
## <a name="stepping-through-code"></a>コードのステップ実行  
 このデバッガは、最も一般的なデバッグ手順の 1 つであるステップ実行 (コードを 1 行ずつ段階的に実行していくこと) をサポートします。 コードをステップ実行するコマンドには、次の 3 つがあります。  
  
-   **ステップ イン**: を使用して、アクティビティにステップ インできます**F11**します。 デバッガーは、任意の定義済みハンドラーにステップ インします。 ハンドラーが定義されていない場合は、アクティビティをステップ オーバーするか、(他のアクティビティを含む) 複合アクティビティの場合には、実行される最初のアクティビティにステップ インします。 デザイナーからのコード ハンドラーにステップ インは、次のアクティビティはサポートされていません: **IfElseActivity**、 **WhileActivity**、 **ConditionedActivityGroup**、または**ReplicatorActivity**します。 これらのアクティビティに関連したハンドラをデバッグするには、明示的なブレークポイントをコード内に配置する必要があります。  
  
-   **ステップ アウト**: を使用して、アクティビティからステップできます**shift キーを押しながら F11**します。 アクティビティからステップ アウトすると、現在のアクティビティとすべての兄弟アクティビティは最後まで実行されます。 その後、デバッガーは現在のアクティビティの親で停止します。 コード ハンドラーからステップ アウトするとき、デバッガーはハンドラーに関連付けられたアクティビティで停止します。  
  
-   **ステップ オーバー**: ステップを使用して、アクティビティ オーバーできます**F10**します。 複合アクティビティをステップ オーバーすると、 デバッガーは複合アクティビティの最初の実行可能な子で停止します。 などをステップ オーバー、複合ではないときに、 **CodeActivity**アクティビティ、デバッガーが次のアクティビティでアクティビティと関連付けられているハンドラーおよび区切りを実行します。 実行されるアクティビティが複合アクティビティの最後の子アクティビティである場合には、デバッガはそれを実行した後、親アクティビティで停止します。  
  
## <a name="attaching-to-a-process"></a>プロセスへのアタッチ  
 プロセスにアタッチすることにより、ワークフローをデバッグするから利用可能なプロセスを選択します。、**選択可能なプロセス**リスト ボックスで、**プロセスにアタッチ** ダイアログ ボックス。 場合**自動: ワークフロー コード**に表示されていない、**にアタッチ**テキスト をクリックし、**選択**します。 **コードの種類の選択**ダイアログ ボックスで、をクリックして**コードの種類をデバッグ**を選択し、**ワークフロー**します。 をクリックし、 **OK**  をクリック**アタッチ**。  
  
## <a name="debugging-with-f5"></a>F5 キーを使ったデバッグ  
 ワークフロー ホスト アプリケーションとワークフロー DLL が存在する場合、Visual Studio プロジェクトなど、ワークフロー アクティビティ ライブラリを使用しているときに、ワークフローをデバッグするには、Visual Studio ソリューション スタートアップ プロジェクトとしてワークフロー DLL プロジェクトを設定する必要があります。使用して**F5**します。 ワークフロー DLL プロジェクトのホスト アプリケーションへのパスを設定することも必要があります**外部プログラムの開始**プロパティ。  
  
 ソリューション エクスプ ローラーでスタートアップ プロジェクトを設定するには、プロジェクト名を右クリックして**スタートアップ プロジェクトとして設定**します。 内のホストにパスを設定する、**外部プログラムの開始**プロパティ、ワークフロー プロジェクトのダブルクリック**プロパティ**ノードをクリックし、ソリューション エクスプ ローラーで、**デバッグ**タブ。**開始動作**を選択します**外部プログラムの開始**しデバッグするワークフローをホストしている、.exe ファイルへのパスを入力します。  
  
 ホスト アプリケーションがスタートアップ プロジェクトとして設定されている場合は、Visual Studio デバッガだけがデバッグ用に起動されます。[!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation は起動されません。 Visual Studio デバッガを使用する場合、C# または Visual Basic コード ブレークポイントだけがヒットします。ワークフロー デザイナで設定されたブレークポイントはヒットしません。 たとえば、デザイナで <xref:System.Workflow.Activities.ParallelActivity> アクティビティに対して設定したブレークポイントは、[!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation が使用される場合にヒットしますが、Visual Studio デバッガが使用される場合はヒットしません。  
  
## <a name="see-also"></a>関連項目  
 [方法: ワークフロー (レガシ) にブレークポイントを設定](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)