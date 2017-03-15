---
title: "Just-In-Time Debugging in Visual Studio (Visual Studio での Just-In-Time デバッグ) | Microsoft Docs"
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
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "デバッグ [Visual Studio], Just-In-Time"
  - "Just-in-time デバッグ"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Just-In-Time Debugging in Visual Studio (Visual Studio での Just-In-Time デバッグ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Just\-In\-Time デバッグは、Visual Studio の外部で実行中のアプリケーションで例外またはクラッシュが発生したときに、Visual Studio を自動的に起動します。  これにより、Visual Studio が実行されていないときにアプリケーションをテストし、問題が発生したときに Visual Studio を使用したデバッグを開始できます。  
  
 Just\-In\-Time デバッグは Windows ストア アプリには実行できません。  Just\-In\-Time デバッグは、ビジュアライザーなどのネイティブ アプリケーションでホストされるマネージ コードには使用できません。  
  
## Just\-In\-Time デバッグの使用  
 Visual Studio をインストールすると、Just\-In\-Time デバッグは既定で有効になります。  Just\-In\-Time デバッグを無効にする\/再び有効にする方法については、「[ステップ実行をマイ コードのみに制限する](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)」を参照してください。  
  
 Just\-In\-Time デバッグが有効な場合、Visual Studio の外部でアプリケーションをテストできます。  クラッシュまたは例外が発生すると、次のようなメッセージがダイアログ ボックスに表示されます。  
  
 ハンドルされていない例外 \('System.TypeInitializationException'\) が terrarium.exe\[3384\] で発生しました。  
  
 このダイアログ ボックスが表示された場合は、次の手順でデバッグを開始できます。  
  
#### エラーが発生したときに Just\-In\-Time デバッグを開始するには  
  
1.  \[Just\-In\-Time デバッグ\] ダイアログ ボックスの **\[利用可能なデバッガー\]** ボックスの一覧で、**\[Visual Studio 2015 の新しいインスタンス\]** をクリックするか、既に実行中の Visual Studio のインスタンスをクリックします。  
  
2.  今後クラッシュが発生した場合に、常に Visual Studio を自動的に使用するには、**\[現在選択されているデバッガーを既定のデバッガーに設定する\]** をクリックします。  
  
3.  デバッグできるコードの種類を選択するには、**\[デバッグ エンジンを手動で選択する\]** をクリックします。  このオプションを選択しないと、プログラムのコードの種類に応じて、適切なデバッグ エンジンが自動的に選択されます。  
  
4.  **\[OK\]** をクリックします。  
  
5.  信頼関係のないコードを使用したアセンブリがアプリケーションに含まれている場合、セキュリティ警告に関するダイアログ ボックスが表示されます。  このダイアログ ボックスでは、デバッグを開始するかどうかを選択できます。  デバッグを開始する前に、コードを信頼できるかどうかを判断します。  このコードは、自分で作成したコードですか。  このコードの作成者は信頼できますか。  アプリケーションをリモート コンピューター上で実行している場合、プロセスの名前を識別できますか。  アプリケーションをローカルに実行している場合でも、それが必ずしもコードを信頼できることにはなりません。  たとえば、Internet Explorer で悪意のある ActiveX コントロールが実行されていることがあります。  このような悪意のあるコードがコンピューター上で実行されている可能性も考慮してください。  デバッグしようとしているコードが信頼できると判断した場合は、**\[デバッグ\]** をクリックします。  それ以外の場合は、**\[Don't Debug\]** \(デバッグしない\) をクリックします。  
  
##  <a name="BKMK_Enabling"></a> Just\-In\-Time デバッグの有効化\/無効化  
 Just\-In\-Time デバッグは、**\[オプション\]** ダイアログ ボックスを使用して有効または無効にできます。  
  
#### Just\-In\-Time デバッグの有効\/無効を切り替えるには  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[オプション\]** ダイアログ ボックスで、**\[デバッグ\]** フォルダーをクリックします。  
  
3.  **\[デバッグ\]** フォルダーで、**\[Just\-In\-Time\]** ページを選択します。  
  
4.  **\[このコードの種類の Just\-In\-Time デバッグを有効にする\]** ボックスで、関連するプログラムの種類 \(**\[マネージ\]**、**\[ネイティブ\]**、または **\[スクリプト\]**\) をクリックし、選択または選択の解除を行います。  
  
     Just\-In\-Time デバッグを有効にした後で無効に切り替えるには、管理者特権で実行する必要があります。  Just\-In\-Time デバッグを有効にするとレジストリ キーが設定され、そのキーを変更するには管理者特権が必要になります。  
  
5.  **\[OK\]** をクリックします。  
  
 既定では、Windows フォーム アプリケーションには、プログラムが正常な状態に戻れば続行できるように、トップ レベルの例外ハンドラーが用意されています。  したがって、Windows フォーム アプリケーションの Just\-In\-Time デバッグを有効にするには、次の追加手順を実行する必要があります。  
  
#### Windows フォームの Just\-In\-Time デバッグを有効化するには  
  
1.  machine.config ファイルまたは `jitDebugging`application.exe.config ファイルの `true` セクションの `system.windows.form` 値を  *に設定します。*  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
2.  さらに、C\+\+ Windows フォーム アプリケーションでは、.config ファイルまたはコード内で `DebuggableAttribute` も設定する必要があります。  [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) を使用し、[\/Og](/visual-cpp/build/reference/og-global-optimizations) を使用せずにコンパイルすると、コンパイラによってこの属性が設定されます。  ただし、最適化されていないリリース ビルドをデバッグする場合は、この属性を自分で設定する必要があります。  そのためには、アプリケーションの AssemblyInfo.cpp ファイルに次の行を追加します。  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     詳細については、「<xref:System.Diagnostics.DebuggableAttribute>」を参照してください。  
  
 Visual Studio がコンピューターからアンインストールされた後でも、Just\-In\-Time デバッグが有効になっている場合があります。  Visual Studio がインストールされていないと、Visual Studio の **\[オプション\]** ダイアログ ボックスから Just\-In\-Time デバッグを無効にすることはできません。  その場合は、Windows レジストリを編集して Just\-In\-Time デバッグを無効にできます。  
  
#### レジストリを編集して Just\-In\-Time デバッグを無効にするには  
  
1.  **\[スタート\]** メニューの \[ファイル名を指定して実行\] をクリックし、「`Regedit.exe`」を実行します。  
  
2.  **\[レジストリ エディター\]** ウィンドウで、次のレジストリ キーを検索し、削除します。  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
3.  コンピューターで 64 ビット オペレーティング システムを実行している場合は、次のレジストリ キーも削除します。  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
4.  誤って他のレジストリ キーを削除または変更しないように注意してください。  
  
5.  **\[レジストリ エディター\]** ウィンドウを閉じます。  
  
## Just\-In\-Time デバッグのエラー  
 Just\-In\-Time デバッグに関連して次のエラー メッセージが表示されることがあります。  
  
-   **クラッシュ プロセスにアタッチできません。  指定されたプログラムは、Windows または MS\-DOS プログラムではありません。**  
  
     このエラーは、Windows 2000 上で別のユーザーとして実行しているプロセスにアタッチしようとすると発生します。  
  
     この問題を解決するには、Visual Studio を起動します。次に、**\[デバッグ\]** メニューから **\[プロセスにアタッチ\]** ダイアログ ボックスを開き、**\[選択可能なプロセス\]** ボックスの一覧からデバッグするプロセスを探します。  目的のプロセスの名前がわからない場合は、**\[Visual Studio Just\-In\-Time デバッガー\]** ダイアログで、プロセス ID を確認します。  そのプロセスを **\[選択可能なプロセス\]** ボックスの一覧から選択し、**\[アタッチ\]** をクリックします。  **\[Visual Studio Just\-In\-Time デバッガー\]** ダイアログの **\[いいえ\]** をクリックして、ダイアログ ボックスを閉じます。  
  
-   **ログオンしているユーザーがいないため、デバッガーを開始できませんでした。**  
  
     このエラーは、コンソールにログオンしているユーザーがいないコンピューターで Just\-In\-Time デバッグが Visual Studio を起動しようとしたときに発生します。  ログオンしているユーザーがいないため、\[Just\-In\-Time デバッグ\] ダイアログ ボックスを表示するためのユーザー セッションがありません。  
  
     この問題を解決するには、コンピューターにログオンします。  
  
-   **クラスは登録されていません。**  
  
     このエラーは、おそらくインストールの問題が原因で登録されていない COM クラスをデバッガーが作成しようとしたことを示します。  
  
     この問題を解決するには、セットアップ ディスクを使って Visual Studio を再インストールするか、既存のインストールを修復します。  
  
## 参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [\[Just\-In\-Time\] \(\[オプション\] ダイアログ ボックス \- \[デバッグ\]\)](../Topic/Just-In-Time,%20Debugging,%20Options%20Dialog%20Box.md)   
 [セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)