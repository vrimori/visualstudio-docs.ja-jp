---
title: Just-In-Time デバッガーを使用したデバッグ |Microsoft Docs
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
ms.openlocfilehash: 99a57f217cc92051f2b85b1b210ce3adf5a189be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058764"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual studio Just-In-Time デバッガーを使用してデバッグします。
ジャストイン タイム デバッグ Visual Studio が自動的に起動 Visual Studio の外部を実行しているアプリケーションで例外またはクラッシュが発生したとき。 これにより、Visual Studio が実行されていない場合に、アプリケーションをテストし、問題が発生したときに、Visual Studio でデバッグを開始することができます。

ジャストイン タイムのデバッグは、Windows デスクトップ アプリに対して機能します。 ユニバーサル Windows アプリの場合は機能しません、ビジュアライザーなどのネイティブ アプリケーションでホストされているマネージ コードは機能しません。

> [!TIP]
> 時間内のみに応答する方法を知りたい場合は、デバッガー ダイアログ ボックスは、「[このトピックの「](../debugger/just-in-time-debugging-in-visual-studio.md)します。

##  <a name="BKMK_Enabling"></a> 有効または無効にするジャスト イン タイムのデバッグ
有効にしたり、時にだけ、Visual Studio からデバッグを無効にする**ツール > オプション** ダイアログ ボックス。

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Just-In-Time デバッグの有効/無効を切り替えるには

1.  管理者特権で Visual Studio を開き (右クリックし、**管理者として実行**)。

    有効にするか、ジャスト イン タイムを無効にすると、レジストリ キーを設定してデバッグし、管理者特権は、そのキーを変更する必要があります。

2. **[ツール]** メニューの **[オプション]** をクリックします。

2.  **オプション** ダイアログ ボックスで、展開、**デバッグ**ノード。

3.  **デバッグ**ノードの **ジャスト イン タイム**します。

    ![有効にするか、JIT デバッグを無効にする](../debugger/media/dbg-jit-enable-or-disable.png "を有効にするか、JIT デバッグを無効にします。")

4.  **Just-In-Time を有効にするは、これらの種類のコードのデバッグ**ボックスをオンまたは関連するプログラムの種類をオフ:**マネージ**、**ネイティブ**、または**スクリプト**.

5.  **[OK]** をクリックします。

Visual Studio がコンピューターからアンインストールされた後でも、Just-In-Time デバッグが有効になっている場合があります。 Visual Studio がインストールされていない場合、時にだけ、Visual Studio からデバッグを無効にすることはできません**オプション** ダイアログ ボックス。 その場合は、Windows レジストリを編集して Just-In-Time デバッグを無効にできます。

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>レジストリを編集して Just-In-Time デバッグを無効にするには

1.  **開始** メニューの検索と実行 `regedit.exe`

2.  **レジストリ エディター**ウィンドウを見つけて、次のレジストリ エントリを削除します。

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   Hkey_local_machine \software\microsoft\\します。NETFramework\DbgManagedDebugger

    ![レジストリ キーの JIT](../debugger/media/dbg-jit-registry.png "JIT レジストリ キー")

3.  お使いのコンピューターで 64 ビットのオペレーティング システムが実行されている場合も、次のレジストリ エントリを削除します。

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   Hkey_local_machine \software\wow6432node\microsoft\\します。NETFramework\DbgManagedDebugger

4.  誤って他のレジストリ キーを削除または変更しないように注意してください。

5.  閉じる、**レジストリ エディター**ウィンドウ。

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Windows フォームの Just-In-Time デバッグを有効化するには

1.  既定では、Windows フォーム アプリケーションには、プログラムが正常な状態に戻れば続行できるように、トップ レベルの例外ハンドラーが用意されています。 たとえば、Windows フォーム アプリケーションでは、未処理の例外をスローする場合は、次のようなダイアログ ボックスが表示されます。

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     ジャスト イン タイムを有効にする Windows フォーム アプリケーションのデバッグには、次の手順を実行する必要があります。

2.  設定、`jitDebugging`値を`true`で、 `system.windows.form` 、machine.config のセクションまたは*\<アプリケーション名 >*。 exe.config ファイル。

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  さらに、C++ Windows フォーム アプリケーションでは、.config ファイルまたはコード内で `DebuggableAttribute` も設定する必要があります。 使用してコンパイルする場合[/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)されず[/Og](/cpp/build/reference/og-global-optimizations)コンパイラでは、この属性を設定できます。 ただし、最適化されていないリリース ビルドをデバッグする場合は、この属性を自分で設定する必要があります。 そのためには、アプリケーションの AssemblyInfo.cpp ファイルに次の行を追加します。

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     詳細については、「<xref:System.Diagnostics.DebuggableAttribute>」を参照してください。

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">使用して、ジャストイン タイムのデバッグ
 このセクションでは、実行可能ファイルは例外をスローするときの動作を示します。

 Visual Studio をインストールする次の手順が必要です。 Visual Studio を持っていない場合は、無料でダウンロードできます、 [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)します。

 そのジャストイン タイムの確認がデバッグ[有効になっている](#BKMK_Enabling)します。

 このセクションの目的で、c# コンソール アプリで行うをスローする Visual Studio、 [NullReferenceException](/dotnet/api/system.nullreferenceexception)します。

 Visual Studio で c# コンソール アプリを作成します (**ファイル > 新規 > プロジェクト > Visual c# > コンソール アプリケーション**) という名前の**ThrowsNullException**します。 Visual Studio でプロジェクトを作成する方法の詳細については、次を参照してください。[チュートリアル: 単純なアプリケーション作成](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)です。

 Visual Studio でプロジェクトを開いたら、Program.cs ファイルを開きます。 Main() メソッドをコンソールには行を表示し、NullReferenceException をスローし、次のコードに置き換えます。

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  この手順で作業するために、[リリース構成](../debugger/how-to-set-debug-and-release-configurations.md)をオフにする必要がある[マイ コードのみ](../debugger/just-my-code.md)します。 Visual Studio で、次のようにクリックします。**ツール > オプション**します。 **オプション**ダイアログ ボックスで、**デバッグ**します。 チェックを外し**マイ コードのみを有効にする**します。

 ソリューションをビルド (Visual Studio で、次のように選択します。**ビルド > ソリューションのリビルド**)。 デバッグまたはリリース構成のいずれかを選択することができます (選択**デバッグ**完全なデバッグ エクスペリエンスのため)。 ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。

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

 **利用可能なデバッガー**が表示される、 **Microsoft Visual Studio の新しいインスタンス<available version>** の行を選択します。 既に選択されていない場合は、ここで選択します。

 ウィンドウの下部にある [ **、選択したデバッガーを使用してデバッグするでしょうか。**、] をクリック**はい**。

 ThrowsNullException プロジェクトは、実行例外をスローする行で停止するいると、Visual Studio の新しいインスタンスで開きます。

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 この時点でのデバッグを開始することができます。 これが実際のアプリケーションの場合、コードが例外をスローして理由を確認する必要があります。

## <a name="just-in-time-debugging-errors"></a>Just-In-Time デバッグのエラー
 プログラムがクラッシュすると、ダイアログ ボックスが表示されない、コンピューターに Windows エラー報告の設定のためこの可能性があります。 詳細については、次を参照してください。[します。WER 設定](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started)します。

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
 [デバッガーのセキュリティ](../debugger/debugger-security.md)[デバッガーの基本事項](../debugger/debugger-basics.md) [Just ポイントイン タイムをデバッグするには、オプション ダイアログ ボックス](../debugger/just-in-time-debugging-options-dialog-box.md)[セキュリティ警告: 信頼されていないユーザーによって所有されているプロセスにアタッチすることができます危険です。以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
