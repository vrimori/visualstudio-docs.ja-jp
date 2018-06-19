---
title: Just-In-Time デバッガーを使用してデバッグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/06/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f01dddf18e93c657d2c69e30a9b4698f4dda796
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268140"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual studio Just-In-Time デバッガーを使用してデバッグします。
ジャスト イン タイム デバッグ Visual Studio が自動的に起動 Visual Studio の外部で実行されるアプリケーション例外またはクラッシュが発生した場合。 これにより、Visual Studio が実行されていない場合、アプリケーションをテストし、問題が発生したときに、Visual Studio でデバッグを開始することができます。

Windows デスクトップ アプリの Just-in-time デバッグは機能します。 ユニバーサル Windows アプリの場合は機能しません、ビジュアライザーなどのネイティブ アプリケーションでホストされているマネージ コードは機能しません。

> [!TIP] 
> 場合は、ジャスト イン タイムに応答する方法を理解するデバッガー ダイアログ ボックスを参照してください[ここ](../debugger/just-in-time-debugging-in-visual-studio.md)です。

##  <a name="BKMK_Enabling"></a> 有効化または無効にジャスト イン タイムのデバッグ  
有効にするにまたは時にのみ、Visual Studio からのデバッグを無効にすることができます**ツール > オプション** ダイアログ ボックス。
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Just-In-Time デバッグの有効/無効を切り替えるには  
  
1.  管理者特権で Visual Studio を開き (を右クリックして**管理者として実行**)。

    有効または無効にジャスト イン タイム レジストリ キーでは、デバッグ設定し、管理者特権は、そのキーを変更する必要があります。
    
2. **[ツール]** メニューの **[オプション]** をクリックします。
  
2.  **オプション** ダイアログ ボックスで、展開、**デバッグ**ノード。  
  
3.  **デバッグ**ノード、**ジャスト イン タイム**です。

    ![有効にするにまたは、JIT デバッグを無効にする](../debugger/media/dbg-jit-enable-or-disable.png "を有効にするか、JIT デバッグを無効にします。") 
  
4.  **コードの種類の有効にする Just-In-Time デバッグを**ボックス、オンまたはオフに関連するプログラムの種類:**マネージ**、**ネイティブ**、または**スクリプト**.    
  
5.  **[OK]** をクリックします。  
  
Visual Studio がコンピューターからアンインストールされた後でも、Just-In-Time デバッグが有効になっている場合があります。 Visual Studio がインストールされていない時にのみ、Visual Studio からデバッグを無効にすることはできません**オプション** ダイアログ ボックス。 その場合は、Windows レジストリを編集して Just-In-Time デバッグを無効にできます。  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>レジストリを編集して Just-In-Time デバッグを無効にするには  
  
1.  **開始**メニューを検索および実行 `regedit.exe`  
  
2.  **レジストリ エディター**  ウィンドウを見つけて、次のレジストリ エントリを削除します。  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\です。NETFramework\DbgManagedDebugger  

    ![レジストリ キーの JIT](../debugger/media/dbg-jit-registry.png "JIT レジストリ キー") 
  
3.  お使いのコンピューターで 64 ビット オペレーティング システムが実行されている場合も、次のレジストリ エントリを削除します。  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\です。NETFramework\DbgManagedDebugger  
  
4.  誤って他のレジストリ キーを削除または変更しないように注意してください。  
  
5.  閉じる、**レジストリ エディター**ウィンドウです。   
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Windows フォームの Just-In-Time デバッグを有効化するには  
  
1.  既定では、Windows フォーム アプリケーションには、プログラムが正常な状態に戻れば続行できるように、トップ レベルの例外ハンドラーが用意されています。 たとえば、Windows フォーム アプリケーションでは、未処理の例外をスローする場合は、次のようなダイアログが表示されます。  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Windows フォーム アプリケーションのデバッグを有効にジャスト イン タイムに、次の手順を実行する必要があります。  
  
2.  設定、`jitDebugging`値を`true`で、 `system.windows.form` 、machine.config のセクションまたは*\<アプリケーション名 >*。 *.exe.config ファイル。  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  さらに、C++ Windows フォーム アプリケーションでは、.config ファイルまたはコード内で `DebuggableAttribute` も設定する必要があります。 コンパイルする場合[/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)されず[/Og](/cpp/build/reference/og-global-optimizations)コンパイラでは、この属性を設定します。 ただし、最適化されていないリリース ビルドをデバッグする場合は、この属性を自分で設定する必要があります。 そのためには、アプリケーションの AssemblyInfo.cpp ファイルに次の行を追加します。  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     詳細については、「<xref:System.Diagnostics.DebuggableAttribute>」を参照してください。  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">ジャスト イン タイム デバッグを使用します。  
 このセクションでは、実行可能ファイルは例外をスローするときの動作を示しています。  
  
 次の手順にインストールされている Visual Studio が必要です。 Visual Studio をお持ちでない場合は、無料ダウンロードできます、 [Visual Studio Community エディション](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)です。  
  
 そのジャスト イン タイムの確認は、デバッグ[有効になっている](#BKMK_Enabling)です。
  
 このセクションの目的で、しましょう c# コンソール アプリケーションをスローする Visual Studio で、 [NullReferenceException](http://msdn.microsoft.com/Library/658af786-d893-4114-a3c5-31c7d586056a)です。  
  
 Visual Studio で、c# コンソール アプリケーションを作成する (**ファイル > 新規 > プロジェクト > Visual c# > コンソール アプリケーション**) という**ThrowsNullException**です。 Visual Studio でプロジェクトの作成の詳細については、次を参照してください。[チュートリアル: 簡単なアプリケーションを作成する](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)です。  
  
 Visual Studio でプロジェクトを開いたら、Program.cs ファイルを開きます。 Main() メソッドをコンソールに行が出力され、NullReferenceException をスローする次のコードに置き換えます。  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  作業するには、この手順の順序で、[リリース構成](../debugger/how-to-set-debug-and-release-configurations.md)、オフにする必要があります[マイ コードのみ](../debugger/just-my-code.md)です。 Visual Studio で、**ツール > オプション**です。 **オプション**ダイアログで、**デバッグ**です。 チェックを外し**マイ コードのみを有効にする**です。  
  
 ソリューションのビルド (Visual Studio で、次のように選択します。**ビルド > ソリューションのリビルド**)。 デバッグまたはリリース構成のいずれかを選択できます (選択**デバッグ**デバッグの完全なエクスペリエンスに)。 ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
 ビルド プロセスでは、実行可能 ThrowsNullException.exe を作成します。 C# プロジェクトを作成したフォルダーの下で見つかります。 **...\ThrowsNullException\ThrowsNullException\bin\Debug**または **...\ThrowsNullException\ThrowsNullException\bin\Release**です。  
  
 ThrowsNullException.exe をダブルクリックします。 次のように、コマンド ウィンドウが表示されます。  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 、数秒後に、エラー ウィンドウが表示されます。  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 クリックしてしないでください**キャンセル**! 、数秒後に 2 つのボタンを表示する必要があります**デバッグ**と**プログラムの終了**です。 をクリックして**デバッグ**です。  
  
> [!CAUTION]
>  アプリに信頼できないコードが含まれている場合と、セキュリティ警告 ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、デバッグを開始するかどうかを選択できます。 デバッグを開始する前に、コードを信頼できるかどうかを判断します。 このコードは、自分で作成したコードですか。 このコードの作成者は信頼できますか。 アプリケーションをリモート コンピューター上で実行している場合、プロセスの名前を識別できますか。 アプリケーションをローカルに実行している場合でも、それが必ずしもコードを信頼できることにはなりません。 お使いのコンピューターで実行されている悪意のあるコードの可能性を考慮します。 デバッグが信頼できるコードをしている方法を決定する場合は、 をクリックして**デバッグ**です。 それ以外の場合、をクリックして**デバッグしない**です。  
  
 **Visual Studio Just-In-Time デバッガー**ウィンドウが表示されます。  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 **利用可能なデバッガー**、表示されます、 **Microsoft Visual Studio の新しいインスタンス<available version>** の行を選択します。 既に選択されていない場合は、ここで選択します。  
  
 ウィンドウの下部にある [ **、選択したデバッガーを使用してデバッグする?**、] をクリックして **[はい]** です。  
  
 実行の例外をスローする行で停止するいると、Visual Studio の新しいインスタンスに ThrowsNullException プロジェクトを開きます。  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 この時点でのデバッグを開始することができます。 これが実際のアプリケーションの場合、コードが例外をスローして理由を確認する必要があります。  
  
## <a name="just-in-time-debugging-errors"></a>Just-In-Time デバッグのエラー  
 プログラムがクラッシュした場合、ダイアログ ボックスが表示されない、コンピューターの Windows エラー報告の設定によりこの可能性があります。 詳細については、次を参照してください。[です。WER の設定](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started)です。  
  
 Just-In-Time デバッグに関連して次のエラー メッセージが表示されることがあります。  
  
-   **クラッシュ プロセスにアタッチできません。指定したプログラムは、Windows または MS-DOS プログラムではないです。**  
  
     このエラーは、別のユーザーとして実行しているプロセスにアタッチしようとしたときに発生します。  
  
     Visual Studio を起動、この問題を回避するために開く、**プロセスにアタッチする**からダイアログ ボックス、**デバッグ**メニューのおよびプロセスでデバッグするときに、検索、**選択可能なプロセス** ボックスの一覧です。 プロセスの名前がわからない場合を見て、 **Visual Studio Just-In-Time デバッガー**ダイアログとプロセス id です。 プロセスを選択して、**選択可能なプロセス**を一覧表示し、をクリックして**アタッチ**です。 **Visual Studio Just-In-Time デバッガー**ダイアログ ボックスで、をクリックして**いいえ** ダイアログ ボックスを閉じます。  
  
-   **ユーザーがログオンしていないために、デバッガーを開始できませんでした。**  
  
     このエラーは、コンソールにログオンしているユーザーがいないコンピューターで Just-In-Time デバッグが Visual Studio を起動しようとしたときに発生します。 ログオンしているユーザーがいないため、[Just-In-Time デバッグ] ダイアログ ボックスを表示するためのユーザー セッションがありません。  
  
     この問題を解決するには、コンピューターにログオンします。  
  
-   **クラスが登録されていません。**  
  
     このエラーは、おそらくインストールの問題が原因で登録されていない COM クラスをデバッガーが作成しようとしたことを示します。  
  
     この問題を解決するには、セットアップ ディスクを使って Visual Studio を再インストールするか、既存のインストールを修復します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [Just-in-time、デバッグ オプション ダイアログ ボックス](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
