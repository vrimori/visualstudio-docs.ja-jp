---
title: ジャストイン タイムは、Visual Studio のデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2fdbbd98833ff43e07b17f605b6c3a105eb3efe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940582"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Just-In-Time Debugging in Visual Studio (Visual Studio での Just-In-Time デバッグ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ジャストイン タイム デバッグ Visual Studio が自動的に起動 Visual Studio の外部を実行しているアプリケーションで例外またはクラッシュが発生したとき。 これにより、Visual Studio が実行されていない場合に、アプリケーションをテストし、問題が発生したときに、Visual Studio でデバッグを開始することができます。

ジャストイン タイムのデバッグは、Windows デスクトップ アプリに対して機能します。 Windows ユニバーサル アプリの場合は機能しません、ビジュアライザーなどのネイティブ アプリケーションでホストされているマネージ コードは機能しません。

## <a name="BKMK_Scenario"></a> 時間内のみでしたがアプリを実行しようとするときにデバッガー ダイアログ ボックスが表示されますか?

表示されたら、Visual Studio でジャスト イン タイムを行う必要がありますアクション デバッガー ダイアログ ボックスでは、何を行うに依存します。

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>ダイアログ ボックスを取り除くだけしたい場合、アプリを通常どおり実行します。

1. (高度なユーザー)Visual Studio のインストールがある (またはが以前にインストールおよび削除する) 場合、[デバッグを使用しないジャスト イン タイム](#BKMK_Enabling)再度アプリを実行しようとします。

2. Internet Explorer で web アプリを実行する場合は、スクリプトのデバッグを無効にします。

    [インターネット オプション] ダイアログ ボックスでスクリプトのデバッグを無効にします。 これからアクセスすることができます、**コントロール パネルの ** / **ネットワークとインターネット** / **インターネット オプション**(正確な手順は、バージョンに依存Windows および Internet Explorer を使用)。

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. エラーを確認したところ、web ページを再度開きます。 これで問題が解決しない場合は、問題を解決する web アプリの所有者にお問い合わせください。

4. 別の種類の Windows アプリを実行している場合は、エラーを修正してから、アプリの固定のバージョンを再インストール、アプリの所有者に連絡する必要があります。

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>解決する方法 (ユーザー詳細) エラーをデバッグする場合

- 必要があります[Visual Studio がインストールされている](https://www.microsoft.com/download/details.aspx?id=48146)デバッグしようとして、エラーに関する詳細情報を表示します。 参照してください[を使用して JIT](#BKMK_Using_JIT)詳しい手順についてはします。 エラーを解決することはできません、アプリを修正する場合は、エラーを解決するのには、アプリの所有者に問い合わせてください。
  
##  <a name="BKMK_Enabling"></a> 有効または無効にするジャスト イン タイムのデバッグ  
 有効にしたり、時にだけ、Visual Studio からデバッグを無効にする**ツール/オプション** ダイアログ ボックス。  
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Just-In-Time デバッグの有効/無効を切り替えるには  
  
1. Visual Studio を開きます。 **[ツール]** メニューの **[オプション]** をクリックします。  
  
2. **オプション**ダイアログ ボックスで、**デバッグ**フォルダー。  
  
3. **デバッグ**フォルダーを選択、**ジャスト イン タイム**ページ。  
  
4. **Just-In-Time を有効にするは、これらの種類のコードのデバッグ**ボックスをオンまたは関連するプログラムの種類をオフ:**マネージ**、**ネイティブ**、または**スクリプト**.  
  
    Just-In-Time デバッグを有効にした後で無効に切り替えるには、管理者特権で実行する必要があります。 Just-In-Time デバッグを有効にするとレジストリ キーが設定され、そのキーを変更するには管理者特権が必要になります。  
  
5. **[OK]** をクリックします。  
  
   Visual Studio がコンピューターからアンインストールされた後でも、Just-In-Time デバッグが有効になっている場合があります。 Visual Studio がインストールされていない場合、時にだけ、Visual Studio からデバッグを無効にすることはできません**オプション** ダイアログ ボックス。 その場合は、Windows レジストリを編集して Just-In-Time デバッグを無効にできます。  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>レジストリを編集して Just-In-Time デバッグを無効にするには  
  
1.  **開始** メニューの検索と実行 `regedit.exe`  
  
2.  **レジストリ エディター**ウィンドウを見つけて次のレジストリ エントリを削除します。  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   Hkey_local_machine \software\microsoft\\します。NETFramework\DbgManagedDebugger  
  
3.  お使いのコンピューターで 64 ビットのオペレーティング システムが実行されている場合も、次のレジストリ エントリを削除します。  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   Hkey_local_machine \software\wow6432node\microsoft\\します。NETFramework\DbgManagedDebugger  
  
4.  誤って他のレジストリ キーを削除または変更しないように注意してください。  
  
5.  閉じる、**レジストリ エディター**ウィンドウ。  
  
> [!NOTE]
>  Just ポイントイン タイム サーバー側のアプリのデバッグを無効にしようとして、次の手順は、問題を解決しない場合は、IIS のアプリケーション設定でサーバー側のデバッグをオフに、再試行してください。  
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Windows フォームの Just-In-Time デバッグを有効化するには  
  
1.  既定では、Windows フォーム アプリケーションには、プログラムが正常な状態に戻れば続行できるように、トップ レベルの例外ハンドラーが用意されています。 たとえば、Windows フォーム アプリケーションでは、未処理の例外をスローする場合は、次のようなダイアログ ボックスが表示されます。  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     ジャスト イン タイムを有効にする Windows フォーム アプリケーションのデバッグには、次の手順を実行する必要があります。  
  
2.  設定、`jitDebugging`値を`true`で、 `system.windows.form` 、machine.config のセクションまたは*\<アプリケーション名 >*。 exe.config ファイル。  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  さらに、C++ Windows フォーム アプリケーションでは、.config ファイルまたはコード内で `DebuggableAttribute` も設定する必要があります。 使用してコンパイルする場合[/Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)されず[/Og](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435)コンパイラでは、この属性を設定できます。 ただし、最適化されていないリリース ビルドをデバッグする場合は、この属性を自分で設定する必要があります。 そのためには、アプリケーションの AssemblyInfo.cpp ファイルに次の行を追加します。  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     詳細については、「 <xref:System.Diagnostics.DebuggableAttribute> 」を参照してください。  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">使用して、ジャストイン タイムのデバッグ  
 このセクションでは、実行可能ファイルは例外をスローするときの動作を示します。  
  
 Visual Studio をインストールする次の手順が必要です。 Visual Studio を持っていない場合は、無料でダウンロードできます、 [Visual Studio 2015 Community Edition](https://www.microsoft.com/download/details.aspx?id=48146)します。  
  
 Visual Studio をインストールすると、Just-In-Time デバッグは既定で有効になります。  
  
 このセクションの目的で、c# コンソール アプリで行うをスローする Visual Studio、<xref:System.NullReferenceException>します。  
  
 Visual Studio で c# コンソール アプリを作成します (**ファイル/新しい/プロジェクト/Visual c#/コンソール アプリケーション**) という名前の**ThrowsNullException**します。 Visual Studio でプロジェクトを作成する方法の詳細については、次を参照してください。[チュートリアル: 単純なアプリケーション作成](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)です。  
  
 Visual Studio でプロジェクトを開いたら、Program.cs ファイルを開きます。 Main() メソッドをコンソールには行を表示し、NullReferenceException をスローし、次のコードに置き換えます。  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  この手順で作業するために、[リリース構成](../debugger/how-to-set-debug-and-release-configurations.md)をオフにする必要がある[マイ コードのみ](../debugger/just-my-code.md)します。 Visual Studio で、次のようにクリックします。**ツール/オプション**します。 **オプション**ダイアログ ボックスで、**デバッグ**します。 チェックを外し**マイ コードのみを有効にする**します。  
  
 ソリューションをビルド (Visual Studio で、次のように選択します。**構築/ソリューションのリビルド**)。 デバッグまたはリリース構成のいずれかを選択できます。 ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
 ビルド プロセスには、実行可能ファイルの ThrowsNullException.exe が作成されます。 C# プロジェクトを作成したフォルダーの下で見つかります。 **...\ThrowsNullException\ThrowsNullException\bin\Debug**または **...\ThrowsNullException\ThrowsNullException\bin\Release**します。  
  
 ThrowsNullException.exe をダブルクリックします。 このようなコマンド ウィンドウが表示されます。  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 数秒後に、後に、エラー ウィンドウが表示されます。  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 クリックしてしないでください**キャンセル**! 数秒後に、2 つのボタンが表示されるはず**デバッグ**と**プログラムの終了**します。 クリックして**デバッグ**します。  
  
> [!CAUTION]
>  アプリケーションが信頼できないコードが含まれる場合と、セキュリティ警告 ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、デバッグを開始するかどうかを選択できます。 デバッグを開始する前に、コードを信頼できるかどうかを判断します。 このコードは、自分で作成したコードですか。 このコードの作成者は信頼できますか。 アプリケーションをリモート コンピューター上で実行している場合、プロセスの名前を識別できますか。 アプリケーションをローカルに実行している場合でも、それが必ずしもコードを信頼できることにはなりません。 お使いのコンピューターで実行されている悪意のあるコードの可能性を検討してください。 デバッグが信頼できること、コードしようとしている場合は、をクリックして**デバッグ**します。 それ以外の場合、をクリックして**デバッグしない**します。  
  
 **Visual Studio Just-In-Time デバッガー**ウィンドウが表示されます。  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 **利用可能なデバッガー**が表示される、 **Microsoft Visual Studio 2015 の新しいインスタンス**の行を選択します。 既に選択されていない場合は、ここで選択します。  
  
 ウィンドウの下部にある [ **、選択したデバッガーを使用してデバッグするでしょうか。**、] をクリック**はい**。  
  
 ThrowsNullException プロジェクトは、実行例外をスローする行で停止するいると、Visual Studio の新しいインスタンスで開きます。  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 この時点でのデバッグを開始することができます。 これが実際のアプリケーションの場合、コードが例外をスローして理由を確認する必要があります。  
  
## <a name="just-in-time-debugging-errors"></a>Just-In-Time デバッグのエラー  
 プログラムがクラッシュすると、ダイアログ ボックスが表示されない、コンピューターに Windows エラー報告の設定のためこの可能性があります。 詳細については、次を参照してください。[します。WER 設定](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx)します。  
  
 Just-In-Time デバッグに関連して次のエラー メッセージが表示されることがあります。  
  
-   **クラッシュ プロセスにアタッチできません。指定したプログラムは、Windows または MS-DOS プログラムではできません。**  
  
     このエラーは、別のユーザーとして実行されているプロセスにアタッチするときに発生します。  
  
     スタート、Visual Studio は、この問題を回避するには、開く、**プロセスにアタッチ** ダイアログ ボックスから、**デバッグ**メニューのおよびデバッグするプロセスを検索、**選択可能なプロセス**一覧。 プロセスの名前がわからない場合を見て、 **Visual Studio Just-In-Time デバッガー**ダイアログとプロセス id です。 プロセスの選択、**選択可能なプロセス**を一覧表示し、をクリックして**アタッチ**します。 **Visual Studio Just-In-Time デバッガー**ダイアログ ボックスで、をクリックして**いいえ**ダイアログ ボックスを閉じます。  
  
-   **ユーザーがログオンしていないために、デバッガーを開始できませんでした。**  
  
     このエラーは、コンソールにログオンしているユーザーがいないコンピューターで Just-In-Time デバッグが Visual Studio を起動しようとしたときに発生します。 ログオンしているユーザーがいないため、[Just-In-Time デバッグ] ダイアログ ボックスを表示するためのユーザー セッションがありません。  
  
     この問題を解決するには、コンピューターにログオンします。  
  
-   **クラスが登録されていません。**  
  
     このエラーは、おそらくインストールの問題が原因で登録されていない COM クラスをデバッガーが作成しようとしたことを示します。  
  
     この問題を解決するには、セットアップ ディスクを使って Visual Studio を再インストールするか、既存のインストールを修復します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [Just-in-time で、デバッグ オプション ダイアログ ボックス](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)



