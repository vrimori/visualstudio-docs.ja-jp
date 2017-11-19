---
title: "Windows Workflow Foundation (レガシ) 用の Visual Studio デバッガーを起動 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f56c7926e949511d90af20ce6789fe662c08e1c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)
このトピックでは、従来の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]で [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションをデバッグするための [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] デバッガーの使用方法について説明します。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
 ほとんどの場合、他の Visual Studio プログラミング言語で書かれたプログラムをデバッグするときと同じようにして、従来のワークフローをデバッグすることができます。 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation を起動するには、次の方法に従います。  
  
-   選択**プロセスにアタッチする**で、**デバッグ** メニューの選択可能なプロセスから実行中のワークフロー インスタンスを選択します。  
  
-   キーを押して**f5 キーを押して**ワークフローのインスタンスを実行を開始するか、ブレークポイントにヒットした後も引き続き実行します。  
  
## <a name="stepping-through-code"></a>コードのステップ実行  
 このデバッガは、最も一般的なデバッグ手順の 1 つであるステップ実行 (コードを 1 行ずつ段階的に実行していくこと) をサポートします。 コードをステップ実行するコマンドには、次の 3 つがあります。  
  
-   **ステップ イン**: を使用して、アクティビティにステップ インできます**F11**です。 デバッガーは、任意の定義済みハンドラーにステップ インします。 ハンドラーが定義されていない場合は、アクティビティをステップ オーバーするか、(他のアクティビティを含む) 複合アクティビティの場合には、実行される最初のアクティビティにステップ インします。 次のアクティビティのデザイナーからコード ハンドラへのステップ インはサポートされていません: **IfElseActivity**、 **WhileActivity**、 **ConditionedActivityGroup**、または**ReplicatorActivity**です。 これらのアクティビティに関連したハンドラをデバッグするには、明示的なブレークポイントをコード内に配置する必要があります。  
  
-   **ステップ アウト**: を使用して、アクティビティからステップできます**Shift F11**です。 アクティビティからステップ アウトすると、現在のアクティビティとすべての兄弟アクティビティは最後まで実行されます。 その後、デバッガーは現在のアクティビティの親で停止します。 コード ハンドラーからステップ アウトするとき、デバッガーはハンドラーに関連付けられたアクティビティで停止します。  
  
-   **ステップ オーバー**: できますをステップ オーバーするアクティビティを使用して、 **F10**です。 複合アクティビティをステップ オーバーすると、 デバッガーは複合アクティビティの最初の実行可能な子で停止します。 ステップ オーバーするとき、非複合など、 **CodeActivity**アクティビティ、デバッガーは次のアクティビティでアクティビティおよび関連するハンドラと改ページを実行します。 実行されるアクティビティが複合アクティビティの最後の子アクティビティである場合には、デバッガはそれを実行した後、親アクティビティで停止します。  
  
## <a name="attaching-to-a-process"></a>プロセスへのアタッチ  
 プロセスにアタッチすることにより、ワークフローをデバッグするにから使用可能なプロセスを選択、**選択可能なプロセス**リスト ボックスで、**プロセスにアタッチする** ダイアログ ボックス。 場合**自動: ワークフロー コード**に表示されていない、**にアタッチ**テキスト ボックスの **選択**です。 **コードの種類の選択**ダイアログ ボックスで、をクリックして**コードの種類をデバッグ**を選択して**ワークフロー**です。 をクリックして**OK**  をクリック**アタッチ**です。  
  
## <a name="debugging-with-f5"></a>F5 キーを使ったデバッグ  
 場合は、ワークフロー ホスト アプリケーションとワークフロー DLL 内にある別の Visual Studio プロジェクトでは、たとえば、ワークフロー アクティビティ ライブラリを使用しているときに、ワークフローをデバッグする Visual Studio ソリューションのスタートアップ プロジェクトとして、ワークフロー DLL プロジェクトを設定する必要があります。使用して**f5 キーを押して**です。 ワークフロー DLL プロジェクトのホスト アプリケーションへのパスを設定することも必要があります**外部プログラムの開始**プロパティです。  
  
 ソリューション エクスプ ローラーでスタートアップ プロジェクトを設定するには、プロジェクト名を右クリックして**スタートアップ プロジェクトとして設定**です。 パス内のホストに設定する、**外部プログラムの開始**プロパティ、ダブルクリックして、ワークフロー プロジェクトの**プロパティ**クリックし、ソリューション エクスプ ローラー内のノード、**デバッグ**タブ**開始動作****外部プログラムの開始**しデバッグするワークフローをホストしている、.exe ファイルへのパスを入力します。  
  
 ホスト アプリケーションがスタートアップ プロジェクトとして設定されている場合は、Visual Studio デバッガだけがデバッグ用に起動されます。[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation は起動されません。 Visual Studio デバッガを使用する場合、C# または Visual Basic コード ブレークポイントだけがヒットします。ワークフロー デザイナで設定されたブレークポイントはヒットしません。 たとえば、デザイナで <xref:System.Workflow.Activities.ParallelActivity> アクティビティに対して設定したブレークポイントは、[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation が使用される場合にヒットしますが、Visual Studio デバッガが使用される場合はヒットしません。  
  
## <a name="see-also"></a>関連項目  
 [方法: ワークフロー (レガシ) 内のブレークポイントを設定](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)