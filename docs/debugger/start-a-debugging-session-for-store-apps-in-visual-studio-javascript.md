---
title: "Visual Studio でのストア アプリのデバッグ セッションの開始 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.installedapppackagelauncher"
  - "vs.debug.error.wwahost_scriptdebuggingdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Visual Studio でのストア アプリのデバッグ セッションの開始 (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Windows と Windows Phone に適用されます](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 このトピックでは、JavaScript と HTML5 で記述された Windows ストア アプリのデバッグ セッションを開始する方法について説明します。1 回のキー入力でデバッグを開始できます。または、特定のシナリオのデバッグ セッションを構成してから、アプリの起動方法を選択できます。  
  
> [!NOTE]
>  XAML および Visual C\#、Visual C\+\+、または Visual Basic で記述されたアプリについては、「[デバッグ セッションの開始 \(VB、C\#、C\+\+、および XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)」を参照してください  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 [このトピックの内容](#BKMK_In_this_topic)  
  
 [デバッグを開始する簡単な方法](#BKMK_The_easy_way_to_start_debugging)  
  
 [デバッグ セッションを構成する](#BKMK_Configure_the_debugging_session)  
  
-   [プロジェクトのデバッグ プロパティ ページを開く](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [ビルド構成オプションを選択する](#BKMK_Choose_the_build_configuration_options)  
  
-   [配置ターゲットを選択する](#BKMK_Choose_the_deployment_target)  
  
-   [使用するデバッガーを選択する](#BKMK_Choose_the_debugger_to_use)  
  
-   [(省略可能) デバッグ セッションでアプリの起動を遅らせる](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  
  
-   [(省略可能) ネットワーク ループバックを無効にする](#BKMK__Optional__Disable_network_loopbacks)  
  
 [デバッグ セッションを開始する](#BKMK_Start_the_debugging_session)  
  
-   [デバッグを開始する (F5)](#BKMK_Start_debugging__F5_)  
  
-   [デバッグは開始する (F5 キー) がアプリの起動は遅らせる](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
 [デバッガーでインストール済みのアプリを起動する](#BKMK_Start_an_installed_app_in_the_debugger)  
  
 [実行中のアプリにデバッガーをアタッチする](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
-   [デバッグ モードで実行するようにアプリを設定する](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
-   [デバッガーをアタッチします。](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> デバッグを開始する簡単な方法  
 ![Windows のみに適用されます](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
1.  Visual Studio でアプリ ソリューションを開きます。  
  
2.  Windows ストア アプリと Windows ストア Phone アプリの両方のプロジェクトがソリューションに含まれる場合、デバッグするプロジェクトがスタートアップ プロジェクトであることを確認します。ソリューション エクスプローラーで、プロジェクトを選択し、コンテキスト メニューの **\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
3.  F5 キーを押します。  
  
 ![Windows Phone のみに適用されます](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Visual Studio によってアプリがビルドされ、アタッチされたデバッガーが起動します。実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。詳細については、「[クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)」を参照してください。  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> デバッグ セッションを構成する  
 スクリプトがコンパイルされていないため、ビルド構成とプラットフォーム設定は適用されません。C\+\+ またはマネージ コンポーネントをデバッグする場合、**\[構成\]** を **\[デバッグ\]** に設定し、**\[構成\]** ダイアログからターゲット プラットフォームを選択します。  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> プロジェクトのデバッグ プロパティ ページを開く  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[構成プロパティ\]** ノードを展開し、**\[デバッグ\]** を選択します。  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> ビルド構成オプションを選択する  
  
1.  **\[構成\]** ボックスの一覧の **\[デバッグ\]** または **\[\(アクティブ\) デバッグ\]** をクリックします。  
  
2.  **\[プラットフォーム\]** ボックスの一覧で、ビルドするターゲット プラットフォームを選択します。ほとんどの場合、**\[Any CPU\]** が最も適しています。  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> 配置ターゲットを選択する  
 Visual Studio コンピューター、ローカル コンピューター上の Visual Studio シミュレーター、またはリモート コンピューター上にアプリを配置してデバッグできます。プロジェクトの **\[デバッグ\]** プロパティ ページにある **\[起動するデバッガー\]** ボックスの一覧からターゲットを選択します。  
  
 ![Windows のみに適用されます](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Windows ストア アプリの場合、**\[ターゲット デバイス\]** ボックスの一覧から次のオプションのいずれかを選択します。  
  
|||  
|-|-|  
|**ローカル コンピューター**|ローカル コンピューターの現在のセッションでアプリをデバッグします。 「[ローカル コンピューターでの Windows ストア アプリの実行](../debugger/run-windows-store-apps-on-the-local-machine.md)」を参照してください。|  
|**シミュレーター**|[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリ用の Visual Studio シミュレーターでアプリをデバッグします。シミュレーターは、ローカル コンピューターでは使用できないデバイスの機能 \(タッチ ジェスチャやデバイスの回転など\) をデバッグできるようにするデスクトップ ウィンドウです。 「[シミュレーターでの Windows ストア アプリの実行](../debugger/run-windows-store-apps-in-the-simulator.md)」を参照してください。|  
|**リモート コンピューター**|ローカル コンピューターにイントラネットを介して接続されているかイーサネット ケーブルを使用して直接接続されているデバイス上のアプリをデバッグします。リモートでデバッグするには、リモート デバイス上に Visual Studio リモート ツールがインストールされ、実行されている必要があります。「[リモート コンピューターでの Windows ストア アプリの実行](../debugger/run-windows-store-apps-on-a-remote-machine.md)」を参照してください。|  
  
 **\[リモート コンピューター\]** をクリックした場合は、次のいずれかの方法でリモート コンピューターの IP アドレスを指定します。  
  
-   **\[コンピューター名\]** ボックスにリモート コンピューターの名前または IP アドレスを入力します。  
  
-   **\[コンピューター名\]** ボックスの下向き矢印をクリックし、**\[検索...\]** を選択します。**\[リモート デバッガー接続の選択\]** ダイアログ ボックスでリモート コンピューターを選択します。  
  
     ![Select Remote Debugger Connection &#40;リモート デバッガーの接続の選択&#41;](../debugger/media/vsrun_pro_selectremotedebuggerdlg.png "VSRUN\_PRO\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  \[リモート デバッガー接続の選択\] ダイアログ ボックスには、ローカル サブネット上にあるコンピューターとイーサネット ケーブルによって Visual Studio コンピューターに直接接続されているコンピューターが表示されます。別のコンピューターを指定するには、**\[コンピューター名\]** ボックスに名前を入力します。  
  
 ![Windows Phone のみに適用されます](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Windows ストア Phone アプリの場合、**\[ターゲット デバイス\]** ボックスの一覧から **\[デバイス\]** またはいずれかのエミュレーターを選択します。  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> 使用するデバッガーを選択する  
 既定では、デバッガーはアプリの JAvaScript コードにアタッチします。JavaScript コードの代わりに、アプリのコンポーネントのネイティブ C\+\+ とマネージ コードをデバッグすることを選択できます。デバッグするコードは、アプリ プロジェクトの **\[デバッグ\]** プロパティ ページの **\[デバッガーの種類\]** の一覧で指定します。  
  
 **\[デバッガーの種類\]** の一覧から次のデバッガーのいずれかを選択します。  
  
|||  
|-|-|  
|**スクリプトのみ**|アプリの JAvaScript コードをデバッグします。マネージ コードとネイティブ コードは無視されます。|  
|**ネイティブのみ**|アプリのネイティブ コードと C\/C\+\+ コードをデバッグします。マネージ コードと JavaScript コードは無視されます。|  
|**スクリプトを利用したネイティブ コード**|アプリのネイティブ C\+\+ コードと JAveScript コードをデバッグします。|  
|**マネージのみ**|アプリのマネージ コードをデバッグします。JavaScript コードとネイティブ C\/C\+\+ コードは無視されます。|  
|**混合 \(マネージとネイティブ\)**|アプリのネイティブ C\/C\+\+ コードとマネージ コードをデバッグします。JavaScript コードは無視されます。|  
  
###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> \(省略可能\) デバッグ セッションでアプリの起動を遅らせる  
 既定では、Visual Studio はデバッグの開始と同時にアプリを起動します。デバッグ セッションは開始するが、アプリの起動は遅らせることもできます。アプリは、\[スタート\] メニューから起動されたとき、アクティブ化コントラクトによって起動されたとき、または別のプロセスやメソッドによって起動されたときに、デバッガー内で起動します。アプリの起動を遅らせることにより、アプリが実行されていないときに発生させるバックグラウンド イベントをアプリ内でデバッグすることもできます。  
  
 アプリ プロジェクトの **\[デバッグ\]** プロパティ ページにある **\[アプリケーションの起動\]** ボックスの一覧で、アプリの起動を遅らせるかどうかを指定します。次のオプションのいずれかを選択します。  
  
-   アプリの起動を遅らせるには、**\[いいえ\]** を選択します。  
  
-   アプリをすぐに起動するには、**\[はい\]** を選択します。  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> \(省略可能\) ネットワーク ループバックを無効にする  
 ![Windows のみに適用されます](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 セキュリティ上の理由から、標準的な方法でインストールされた Windows ストア アプリは、インストール先のデバイスに対してネットワーク呼び出しを行うことはできません。既定では、Visual Studio による配置では、配置されたアプリに対するこの規則の適用は免除されます。この免除によって、1 台のコンピューター上で通信プロシージャをテストできます。Windows ストアにアプリを送信する前に、この免除なしでアプリをテストする必要があります。  
  
 ネットワーク ループバックの免除を削除するには、**\[デバッグ\]** プロパティ ページの **\[ネットワーク ループバックの許可\]** ボックスの一覧の **\[いいえ\]** をクリックします。  
  
##  <a name="BKMK_Start_the_debugging_session"></a> デバッグ セッションを開始する  
  
###  <a name="BKMK_Start_debugging__F5_"></a> デバッグを開始する \(F5\)  
 **\[デバッグ\]** メニューの **\[デバッグの開始\]** をクリックする \(キーボードの場合は F5 キーを押す\) と、デバッガーがアタッチされた状態でアプリが起動します。実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> デバッグは開始する \(F5 キー\) がアプリの起動は遅らせる  
 デバッグ モードで実行されるようにアプリを設定し、デバッガー以外の方法でアプリを起動できます。たとえば、\[スタート\] メニューからのアプリの起動をデバッグしたり、アプリを起動せずにアプリのバックグラウンド プロセスをデバッグしたりできます。アプリの起動を遅らせるには、次の手順を実行します。  
  
1.  アプリ プロジェクト プロパティの **\[デバッグ\]** ページで、**\[アプリケーションの起動\]** ボックスの一覧から **\[いいえ\]** を選択します。  
  
2.  **\[デバッグ\]** メニューの **\[デバッグの開始\]** をクリックします \(キーボードの場合: F5\)。  
  
3.  \[スタート\] メニュー、実行コントラクト、または別のプロシージャからアプリを起動します。  
  
 アプリがデバッグ モードで起動します。実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。  
  
 バックグラウンド タスクのデバッグの詳細については、「[Windows ストアの中断イベント、再開イベント、およびバックグラウンド イベントのトリガー](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)」を参照してください。  
  
##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> デバッガーでインストール済みのアプリを起動する  
 F5 キーを使用してデバッグを開始すると、Visual Studio はアプリをビルドして配置し、デバッグ モードで実行されるようにアプリを設定してから起動します。デバイスに既にインストールされているアプリを起動するには、\[インストールされているアプリケーション パッケージのデバッグ\] ダイアログ ボックスを使用します。この方法は、Windows ストアからインストールされたアプリをデバッグする必要がある場合や、アプリのソース ファイルはあってもアプリの Visual Studio プロジェクトがない場合に役立ちます。Visual Studio プロジェクトやソリューションを使用しないカスタム ビルド システムがこれに該当します。  
  
 アプリはローカル デバイスにインストールすることも、リモート デバイスにインストールすることもできます。 アプリをすぐに起動できます。また、アプリを別のプロセスや方法で起動したときに \(\[スタート\] メニューからの起動や、アクティブ化コントラクトによる起動など\)、デバッガーで実行するようにアプリを設定することもできます。アプリを起動せずにバックグラウンド プロセスをデバッグする場合は、デバッグ モードで実行されるようにアプリを設定できます。詳細については、「[Windows ストアの中断イベント、再開イベント、およびバックグラウンド イベントのトリガー](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)」を参照してください。  
  
 インストール済みのアプリがデバッグ モードで実行されるように設定するには、次の手順を実行します。  
  
> [!NOTE]
>  この手順は、アプリが実行されていないときに開始してください。  
  
1.  **\[デバッグ\]** メニューの **\[インストールされているアプリケーション パッケージのデバッグ\]** をクリックします。  
  
2.  一覧から次のいずれかのオプションを選択します。  
  
    |||  
    |-|-|  
    |**ローカル コンピューター**|ローカル コンピューターの現在のセッションでアプリをデバッグします。 「[ローカル コンピューターでの Windows ストア アプリの実行](../debugger/run-windows-store-apps-on-the-local-machine.md)」を参照してください。|  
    |**シミュレーター**|[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリ用の Visual Studio シミュレーターでアプリをデバッグします。シミュレーターは、ローカル コンピューターでは使用できないデバイスの機能 \(タッチ ジェスチャやデバイスの回転など\) をデバッグできるようにするデスクトップ ウィンドウです。 「[シミュレーターでの Windows ストア アプリの実行](../debugger/run-windows-store-apps-in-the-simulator.md)」を参照してください。|  
    |**リモート コンピューター**|ローカル コンピューターにイントラネットを介して接続されているかイーサネット ケーブルを使用して直接接続されているデバイス上のアプリをデバッグします。リモートでデバッグするには、リモート デバイス上に Visual Studio リモート ツールがインストールされ、実行されている必要があります。「[リモート コンピューターでの Windows ストア アプリの実行](../debugger/run-windows-store-apps-on-a-remote-machine.md)」を参照してください。|  
  
3.  **\[インストールされているアプリケーション パッケージ\]** ボックスの一覧からアプリを選択します。  
  
4.  **\[このコードの種類をデバッグ\]** ボックスの一覧から、使用するデバッグ エンジンを選択します。  
  
5.  \(省略可能\) 他の方法で起動したアプリをデバッグするときや、バックグラウンド プロセスをデバッグするときは、**\[起動しないが、開始時にコードをデバッグ\]** を選択します。  
  
 **\[開始\]** をクリックすると、アプリが起動するか、デバッグ モードで実行するように設定されます。  
  
##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 実行中のアプリにデバッガーをアタッチする  
 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリにデバッガーをアタッチするには、デバッグ可能パッケージ マネージャーを使用して、デバッグ モードで実行するようにアプリを設定する必要があります。デバッグ可能パッケージ マネージャーは、Visual Studio リモート ツールと共にインストールされます。  
  
 アプリへのデバッガーのアタッチは、インストール済みのアプリ \(Windows ストアからインストールされたアプリなど\) をデバッグする場合に役立ちます。アタッチは、アプリのソース ファイルはあるが、アプリの Visual Studio プロジェクトがない場合に必要です。Visual Studio プロジェクトやソリューションを使用しないカスタム ビルド システムがこれに該当します。  
  
 アプリをアタッチするには:  
  
1.  デバッグ モードで実行するようにアプリを設定するこれは、アプリが実行されていないときに行う必要があります。  
  
2.  アプリを起動します。アプリの起動は、\[スタート\] メニュー、実行コントラクト、または他の方法で実行できます。  
  
3.  実行中のアプリにデバッガーをアタッチします。  
  
###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> デバッグ モードで実行するようにアプリを設定する  
  
1.  アプリをインストールするデバイスに Visual Studio リモート ツールをインストールします。「[Remote Tools のインストール](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools)」を参照してください。  
  
2.  \[スタート\] メニューで`Debuggable Package Manager`を検索して起動します。  
  
     AppxDebug コマンドレット用に適切に構成された PowerShell ウィンドウが表示されます。  
  
3.  アプリのデバッグを有効にするには、アプリの PackageFullName 識別子を指定する必要があります。PackageFullName を含むすべてのアプリの一覧を表示するには、PowerShell プロンプトに「`Get-AppxPackage`」と入力します。  
  
4.  PowerShell プロンプトに「`Enable-AppxDebug` *PackageFullName*」と入力します。*PackageFullName* はアプリの PackageFullName 識別子です。  
  
###  <a name="BKMK_Attach_the_debugger"></a> デバッガーをアタッチします。  
  
> [!TIP]
>  JavaScript アプリは、wwahost.exe プロセスのインスタンスで実行されます。アプリにアタッチする際に他の JavaScript アプリが実行されている場合、そのアプリが実行されている wwahost.exe の数値型プロセス ID \(PID\) を確認する必要があります。  
>   
>  このような状況に対処する最も簡単な方法は、他の JAvaScript アプリをすべて閉じることです。別の方法として、アプリを起動する前に Windows タスク マネージャーを開き、wwahost.exe プロセスの ID を確認できます。アタッチするプロセスを **\[選択可能なプロセス\]** ダイアログ ボックスで指定する場合、アプリの wwahost.exe の ID は、以前に確認した ID と異なる ID になります。  
  
 デバッガーをアタッチするには:  
  
1.  **\[デバッグ\]** メニューの **\[プロセスにアタッチ\]** をクリックします。  
  
     **\[プロセスにアタッチ\]** ダイアログ ボックスが表示されます。  
  
2.  リモート デバイス上のアプリにアタッチするには、**\[修飾子\]** ボックスにリモート デバイスを指定します。次の操作を行うことができます。  
  
    -   **\[修飾子\]** ボックスに名前を入力します。  
  
    -   **\[修飾子\]** ボックスの下向き矢印をクリックし、デバイスの一覧から、前にアタッチしたデバイスを選択します。  
  
    -   **\[検索\]** をクリックし、ローカル サブネットのデバイスの一覧からデバイスを選択します。  
  
3.  デバッグするコードの種類を **\[アタッチ先\]** ボックスに指定します。  
  
     **\[選択\]** をクリックし、次のいずれかを実行します。  
  
    -   **\[デバッグするコードの種類を自動的に判断する\]** をクリックします。  
  
    -   **\[次のコードの種類をデバッグする\]** をクリックし、一覧から 1 つ以上の型を選択します。  
  
4.  **\[選択可能なプロセス\]** の一覧から、適切な **wwahost.exe** プロセスを選択します。**\[タイトル\]** 列を使用して、アプリを特定します。  
  
5.  **\[アタッチ\]** をクリックします。  
  
 Visual Studio によって、デバッガーがプロセスにアタッチされます。実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。  
  
## 参照  
 [デバッグ セッションでの実行制御 \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)   
 [Windows ストアの中断イベント、再開イベント、およびバックグラウンド イベントのトリガー](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Visual Studio でのアプリのデバッグ](../debugger/debug-store-apps-in-visual-studio.md)