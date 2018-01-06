---
title: "複数のプロセスのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7d0aaa97009662000bf1376c1684d9ca41a7133a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debug-multiple-processes"></a>複数プロセスをデバッグする
プロセスのデバッグを開始、プロセスの切り替え、中断し実行を続行、ソースのステップ実行、デバッグを停止および終了/プロセスからデタッチする方法を次に示します。  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>複数のプロセスの実行動作を構成します。  
 既定では、複数のプロセスがデバッガーで実行されているとき、デバッガーの中断、ステップ実行、停止のコマンドは通常、すべてのプロセスに影響を与えます。 たとえば、1 つのプロセスがブレークポイントで中断されると、他のすべてのプロセスの実行も一時停止されます。 コマンドの実行対象をより詳細に制御するために、この既定の動作を変更できます。  
  
1.  をクリックして**デバッグ > オプションと設定**です。  
  
2.  **デバッグ**、**全般** ページで、クリア、 **1 つのプロセスがブレークするときに、すべてのプロセスを中断**チェック ボックスをオンします。  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>ソースとシンボル (.pdb) ファイルを検索します。  
 プロセスのソース コードを処理するために、デバッガーにはプロセスのソース ファイルとシンボル ファイルへのアクセスが必要になります。 参照してください[シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)です。  
  
 プロセスのファイルにアクセスすることはできない場合、は、[逆アセンブル] ウィンドウを使用して移動できます。 参照してください[する方法: [逆アセンブル] ウィンドウを使用して](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>VS ソリューション内の複数のプロセスの開始、プロセスにアタッチする、デバッガーでプロセスが自動的に開始  
  
-   [Visual Studio ソリューション内の複数のプロセスのデバッグを開始します。](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution)  
  
-   [スタートアップ プロジェクトを変更します。](#BKMK_Change_the_startup_project)  
  
-   [ソリューション内の特定のプロジェクトを開始します。](#BKMK_Start_a_specific_project_in_a_solution)  
  
-   [ソリューション内の複数のプロジェクトを開始します。](#BKMK_Start_multiple_projects_in_a_solution)  
  
-   [プロセスにアタッチします。](#BKMK_Attach_to_a_process)  
  
-   [デバッガーでプロセスが自動的に開始します。](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  デバッガーは、子プロジェクトが同じソリューション内にある場合でも、デバッグ対象のプロセスによって開始された子プロセスに自動的にアタッチされません。 子プロセスをデバッグするには:   
>   
>  -   子プロセスが開始された後、そのプロセスにアタッチします。  
>   
>      - または -  
> -   デバッガーの新しいインスタンスで子プロセスが自動的に開始されるように Windows を構成します。  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Visual Studio ソリューション内の複数のプロセスのデバッグを開始します。  
 Visual Studio ソリューション内に独立して実行できる複数のプロジェクト (個別のプロセスで実行されるプロジェクト) があるときは、デバッガーによって起動されるプロジェクトを選択できます。  
  
 ![プロジェクトのスタートアップの種類を変更する](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a>スタートアップ プロジェクトを変更します。  
 ソリューションのスタートアップ プロジェクトを変更するには、ソリューション エクスプ ローラーでプロジェクトを選択し、**スタートアップ プロジェクトとして設定**コンテキスト メニュー。  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a>ソリューション内の特定のプロジェクトを開始します。  
 既定のスタートアップ プロジェクトを変更することがなく、ソリューションのプロジェクトを開始、ソリューション エクスプ ローラーでプロジェクトを選択し、**デバッグ**コンテキスト メニュー。 選択できるよう**新しいインスタンスを開始**または**新しいインスタンスにステップ イン**です。  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [VS ソリューション内の複数のプロセスの開始、プロセスにアタッチする、デバッガーでプロセスが自動的に開始](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a>ソリューション内の複数のプロジェクトを開始します。  
  
1.  ソリューション エクスプ ローラーでソリューションを選択し、**プロパティ**コンテキスト メニューの します。  
  
2.  選択**共通プロパティ**、**スタートアップ プロジェクト**上、**プロパティ** ダイアログ ボックス。  
  
3.  各プロジェクトを変更するのには、いずれかを選択**開始**、**デバッグなしで開始**、または**None**です。  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [VS ソリューション内の複数のプロセスの開始、プロセスにアタッチする、デバッガーでプロセスが自動的に開始](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a>プロセスにアタッチします。  
 デバッガーのことにも*アタッチ*Visual Studio の外部プロセスで実行されているプログラムでは、リモート デバイスで実行されているプログラムを含むです。 プログラムにアタッチした後、デバッガーの実行コマンドを使用したり、プログラムの状態をチェックしたりできます。 プログラムのチェック機能は、デバッグ情報付きでビルドされたプログラムかどうか、プログラムのソース コードにアクセスできるかどうか、および共通言語ランタイムの JIT コンパイラがデバッグ情報を追跡しているかどうかによって限定される場合があります。  
  
 参照してください[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)詳細についてはします。  
  
 **ローカル コンピューターで実行されているプロセスにアタッチします。**  
  
 をクリックして**デバッグ > プロセスにアタッチする**です。 **プロセスにアタッチする** ダイアログ ボックスからプロセスを選択、**選択可能なプロセス**一覧をクリックして**アタッチ**です。  
  
 ![プロセスにアタッチ ダイアログ ボックス](../debugger/media/dbg_attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>デバッガーでプロセスが自動的に開始します。  
 場合によっては、別のプロセスで起動されたプログラムのスタートアップ コードをデバッグする必要があります。 たとえば、サービスやカスタムのセットアップ動作などです。 このような場合、アプリケーションの起動時にデバッガーを起動して自動的にアタッチできます。  
  
1.  レジストリ エディターを起動 (**regedit.exe**)。  
  
2.  移動し、 **hkey_local_machine \software\microsoft\windows nt \currentversion\image File Execution Options**フォルダーです。  
  
3.  デバッガーで起動するアプリのフォルダーを選択します。  
  
     アプリの名前が表示されない場合、子フォルダーとして、選択**Image File Execution Options**を選択し**新規**、**キー**コンテキスト メニューの します。 新しいキーを選択し、選択**の名前を変更**ショートカット メニューで、アプリの名前を入力します。  
  
4.  App フォルダーのコンテキスト メニューを開き、次のように選択します。**新規**、**文字列値**です。  
  
5.  新しい値の名前を変更**新しい値**に`debugger`です。  
  
6.  デバッガー エントリのコンテキスト メニューを開き、次のように選択します。**変更**です。  
  
7.  [文字列の編集] ダイアログ ボックスで、次のように入力します。`vsjitdebugger.exe`で、**値のデータ**ボックス。  
  
     ![[編集] ダイアログ ボックスの文字列](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
 ![Regedit.exe の自動デバッガー開始エントリ](../debugger/media/dbg_execution_automaticstart_result.png "DBG_Execution_AutomaticStart_Result")  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>プロセスを切り替える、中断/続行、ソースをステップ実行  
  
-   [プロセスの切り替え](#BKMK_Switch_between_processes)  
  
-   [中断、ステップ、およびコマンドを続行](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a>プロセスの切り替え  
 デバッグ中には複数のプロセスにアタッチできますが、デバッガーでアクティブになっているプロセスは常に 1 つだけです。 アクティブなを設定することができますか*現在*やデバッグの場所 ツールバーで、プロセス、**プロセス**ウィンドウです。 プロセス間で切り替えるには、両方のプロセスが中断モードであることが必要です。  
  
 **現在のプロセスを設定するには**  
  
-   [デバッグの場所] ツールバーで、選択**プロセス**を表示する、**プロセス**ボックスの一覧です。 現在のプロセスとして指定するプロセスを選択します。  
  
     ![プロセス間を切り替える](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
     場合、**デバッグの場所**ツールバーが表示されていない、選択**ツール**、**カスタマイズ**です。 **ツールバー**  タブで、選択**デバッグの場所**です。  
  
-   開く、**プロセス**ウィンドウ (ショートカット**Ctrl + Alt + Z**)、現在のプロセスとして設定するプロセスを検索し、ダブルクリックします。  
  
     ![[プロセス] ウィンドウ](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")  
  
     現在のプロセスが黄色の矢印でマークされます。  
  
 プロジェクトを切り替えると、そのプロジェクトがデバッグ対象の現在のプロセスに設定されます。 表示するすべてのデバッガー ウィンドウに、現在のプロセスの状態が表示され、すべてのステップ実行コマンドは現在のプロセスにのみ影響を与えます。  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [プロセスを切り替える、中断/続行、ソースをステップ実行](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a>中断、ステップ、およびコマンドを続行  
  
> [!NOTE]
>  既定では、中断、続行、ステップ実行のコマンドはデバッグ中のすべてのプロセスに影響を与えます。 この動作を変更するを参照してください[複数のプロセスの実行動作を構成します。](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**コマンド**|**1 つのプロセスがブレークするときに、すべてのプロセスを中断します。**<br /><br /> オンにした場合 (既定)|**1 つのプロセスがブレークするときに、すべてのプロセスを中断します。**<br /><br /> オフにした場合|  
|**デバッグ**メニュー。<br /><br /> -   **[すべて中断]**|すべてのプロセスが中断されます。|すべてのプロセスが中断されます。|  
|**デバッグ**メニュー。<br /><br /> -   **続行**|すべてのプロセスが再開されます。|一時停止中のすべてプロセスが再開されます。|  
|**デバッグ**メニュー。<br /><br /> -   **ステップ イン**<br />-   **ステップ オーバー**<br />-   **[ステップ アウト]**|現在のプロセスのステップ実行中にすべてのプロセスが実行されます。<br /><br /> その後、すべてのプロセスが中断されます。|現在のプロセスがステップ実行されます。<br /><br /> 一時停止中のプロセスが再開されます。<br /><br /> 実行中のプロセスが続行されます。|  
|**デバッグ**メニュー。<br /><br /> -   **現在のプロセスにステップ イン**<br />-   **現在のプロセスが細かく手順**<br />-   **[ステップ アウト] 現在のプロセス**|N/A|現在のプロセスがステップ実行されます。<br /><br /> 他のプロセスの既存の状態 (一時停止中または実行中) が維持されます。|  
|ソース ウィンドウ<br /><br /> -   **ブレークポイント**|すべてのプロセスが中断されます。|ソース ウィンドウのプロセスのみ中断されます。|  
|ソース ウィンドウのコンテキスト メニュー: <br /><br /> -   **カーソルまでを実行します。**<br /><br /> ソース ウィンドウのプロセスは現在のプロセスであることが必要です。|ソース ウィンドウのプロセスがカーソル位置まで実行されてから中断されている間に、すべてのプロセスが実行されます。<br /><br /> その後、他のすべてのプロセスが中断されます。|ソース ウィンドウのプロセスはカーソル位置まで実行されます。<br /><br /> 他のプロセスの既存の状態 (一時停止中または実行中) が維持されます。|  
|**プロセス**ウィンドウ コンテキスト メニュー。<br /><br /> -   **プロセスのブレーク**|N/A|選択したプロセスが中断されます。<br /><br /> 他のプロセスの既存の状態 (一時停止中または実行中) が維持されます。|  
|**プロセス**ウィンドウ コンテキスト メニュー。<br /><br /> -   **プロセスを続行します。**|N/A|選択したプロセスが再開されます。<br /><br /> 他のプロセスの既存の状態 (一時停止中または実行中) が維持されます。|  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [プロセスを切り替える、中断/続行、ソースをステップ実行](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>デバッグの停止を終了する/プロセスからデタッチします。  
  
-   [停止、終了、およびデタッチのコマンド](#BKMK_Stop__terminate__and_detach_commands)  
  
 既定を選択すると**デバッグ**、**デバッグの停止**デバッガーが終了するか、プロセスを開いた方法に応じて、すべてのプロセスからデタッチ複数のプロセスは、デバッガーで開いている、ときに、デバッガー:  
  
-   現在のプロセスがデバッガーで開始された場合、そのプロセスは終了します。  
  
-   デバッガーを現在のプロセスにアタッチした場合、デバッガーはプロセスからデタッチされ、プロセスは実行中のままになります。  
  
 たとえば、Visual Studio ソリューションからプロセスのデバッグを開始する場合、既に実行されている別のプロセスにアタッチし、[**デバッグの停止]**では、デバッグ セッションを終了、Visual Studio で開始されたプロセス終了中に関連付けられているプロセスが実行したままにします。 次の手順を使用してデバッグの停止方法を制御できます。  
  
> [!NOTE]
>  **1 つのプロセスがブレークするときに、すべてのプロセスをブレーク**オプションには影響しませんまたはデバッグを終了して、プロセスからのデタッチを停止します。  
  
 **デバッグの停止と、個別のプロセスにどのように影響する方法を変更するには**  
  
-   開く、**プロセス**ウィンドウ (ショートカット**Ctrl + Alt + Z**)。 プロセスを選択し、オンまたはオフ、**デバッグの停止時にデタッチ**チェック ボックスをオンします。  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a>停止、終了、およびデタッチのコマンド  
  
|||  
|-|-|  
|**コマンド**|**説明**|  
|**デバッグ**メニュー。<br /><br /> -   **デバッグの停止します。**|によって動作が変更されない限り**プロセス**ウィンドウ**デバッグの停止時にデタッチ**オプション。<br /><br /> 1.デバッガーによって開始されたプロセスが終了します。<br />2.アタッチ中のプロセスがデバッガーからデタッチされます。|  
|**デバッグ**メニュー。<br /><br /> -   **[すべて中止]**|すべてのプロセスが終了します。|  
|**デバッグ**メニュー。<br /><br /> -   **[すべてデタッチ]**|すべてのプロセスからデバッガーがデタッチされます。|  
|**プロセス**ウィンドウ コンテキスト メニュー。<br /><br /> -   **デタッチ (プロセス)**|選択したプロセスからデバッガーがデタッチされます。<br /><br /> 他のプロセスの既存の状態 (一時停止中または実行中) が維持されます。|  
|**プロセス**ウィンドウ コンテキスト メニュー。<br /><br /> -   **プロセスが終了します。**|選択したプロセスが終了します。<br /><br /> 他のプロセスの既存の状態 (一時停止中または実行中) が維持されます。|  
|**プロセス**ウィンドウ コンテキスト メニュー。<br /><br /> -   **デバッグの停止時にデタッチ**|動作を切り替えます**デバッグ**、**デバッグの停止**選択されたプロセスの。<br /><br /> -チェックされます。 デバッガーはプロセスからデタッチします。<br />-消去: プロセスが終了します。|  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [デバッグの停止を終了する/プロセスからデタッチします。](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![ページのトップへ](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
## <a name="see-also"></a>参照  
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [実行中のプロセスをアタッチします。](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)   
 [ジャスト イン タイム デバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)