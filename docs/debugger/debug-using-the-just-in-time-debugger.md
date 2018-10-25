---
title: Just-In-Time デバッガーを使用したデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 09/24/18
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
ms.openlocfilehash: f66d3fdcd400be9356776647b0ead118e83d7108
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382748"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual studio Just-In-Time デバッガーを使用してデバッグします。

ジャストイン タイム デバッグ Visual Studio を起動自動的にすると外部の Visual Studio のエラーまたはクラッシュを実行中のアプリ。 Just ポイントイン タイムのデバッグ、Visual Studio は、外のアプリをテストでき、問題が発生したときに、デバッグを開始する Visual Studio を開きます。

ジャストイン タイムのデバッグは、Windows デスクトップ アプリに対して機能します。 ユニバーサル Windows アプリ、またはビジュアライザーなどのネイティブ アプリケーションでホストされているマネージ コードは機能しません。

> [!TIP]
> 停止するを表示するには、Just-In-Time デバッガー ダイアログ ボックスがない Visual Studio がインストールされているを参照してください、たい場合[Just-In-Time デバッガーを無効にする](../debugger/just-in-time-debugging-in-visual-studio.md)します。 Visual Studio がインストールされている 1 回場合、は、する必要があります[Windows レジストリからデバッグを使用しないジャスト イン タイム](#disable-just-in-time-debugging-from-the-windows-registry)します。 

##  <a name="BKMK_Enabling"></a> 有効または無効にするジャスト イン タイムが Visual Studio のデバッグ

>[!NOTE]
>有効または時間でのみデバッグを無効にするは、管理者として Visual Studio する実行する必要があります。 有効にするか、ジャスト イン タイムを無効にすると、レジストリ キーを設定してデバッグし、管理者特権は、そのキーを変更する必要があります。 管理者として Visual Studio を開くには、Visual Studio アプリケーションを右クリックし、選択**管理者として実行**します。 

時にだけ、Visual Studio からデバッグを構成する**ツール** > **オプション**(または**デバッグ** > **のオプション**)ダイアログ ボックス。 

**有効または無効にするジャスト イン タイムのデバッグします。**

1. **ツール**または**デバッグ**メニューの **オプション** > **デバッグ** >  **ジャストイン タイム**します。

   ![有効にするか、JIT デバッグを無効にする](../debugger/media/dbg-jit-enable-or-disable.png "を有効にするか、JIT デバッグを無効にします。")

1. **コードの種類の有効にする Just-In-Time デバッグを**ボックスに、時にのみをデバッグするデバッグするコードの種類を選択:**マネージ**、**ネイティブ**、や**スクリプト**します。
   
1. **[OK]** を選択します。

時にのみ有効にした場合、デバッガーが、それが開かない場合は、アプリのクラッシュやエラーを参照してください[のトラブルシューティングの Just-In-Time デバッグ](#jit_errors)します。

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>時にのみ Windows レジストリからデバッグを無効にします。

Visual Studio がコンピューターからアンインストールされた後でも、Just-In-Time デバッグが有効になっている場合があります。 Visual Studio がインストールされていない場合は、時にのみ Windows レジストリを編集してデバッグを無効にすることができます。

**時にのみ、レジストリを編集してデバッグを無効にします。**

1.  Windows から**開始**メニュー、実行、**レジストリ エディター** (*regedit.exe*)。

2.  **レジストリ エディター**ウィンドウを見つけて、次のレジストリ エントリを削除します。

    -   **Hkey_local_machine \software\microsoft\\します。NETFramework\DbgManagedDebugger**

    -   **Hkey_local_machine \software\microsoft\windows NT\CurrentVersion\AeDebug\Debugger**

    ![レジストリ キーの JIT](../debugger/media/dbg-jit-registry.png "JIT レジストリ キー")

3.  お使いのコンピューターで 64 ビットのオペレーティング システムが実行されている場合も、次のレジストリ エントリを削除します。

    -   **Hkey_local_machine \software\wow6432node\microsoft\\します。NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    削除または他のレジストリ キーの変更を確認します。

5.  閉じる、**レジストリ エディター**ウィンドウ。

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>ジャスト イン タイムを有効にする Windows フォームのデバッグ

既定では、Windows フォーム アプリは、アプリにその回復できる場合に実行を継続する最上位の例外ハンドラーがあります。 Windows フォーム アプリでは、未処理の例外をスローする場合は、次のダイアログ ボックスが表示されます。

![Windows フォームのハンドルされない例外](../debugger/media/windowsformsunhandledexception.png "Windows フォームのハンドルされない例外")

時間で Just 標準の Windows フォーム エラーを処理ではなくデバッグを有効にするには、これらの設定を追加します。

-  `system.windows.forms`のセクション、 *machine.config*または*\<アプリ名 >. exe.config*ファイル、設定、`jitDebugging`値を`true`:
    
    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```
    
-  C++ Windows フォーム アプリケーションでも設定`DebuggableAttribute`に`true`で、 *.config*ファイルまたはコード。 使用してコンパイルする場合[/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)されず[/Og](/cpp/build/reference/og-global-optimizations)コンパイラでは、この属性を設定できます。 最適化されていないリリース ビルドをデバッグする場合は、ただし、する必要があります設定`DebuggableAttribute`アプリの次の行を追加することで*AssemblyInfo.cpp*ファイル。

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```
   
   詳細については、「 <xref:System.Diagnostics.DebuggableAttribute> 」を参照してください。

## <a name="BKMK_Using_JIT"></a>ジャスト イン タイムを使用して、デバッグ
 この例では、時にのみアプリがエラーをスローするときにデバッグについて説明します。

 - Visual Studio をインストールする次の手順が必要です。 Visual Studio を持っていない場合は、無料でダウンロードできます、 [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)します。
   
 - 時間だけのことを確認のデバッグは[有効になっている](#BKMK_Enabling)で**ツール** > **オプション** > **デバッグ** > **ジャストイン タイム**します。

この例では、することになります、C#をスローする Visual Studio でコンソール アプリを[NullReferenceException](/dotnet/api/system.nullreferenceexception)します。

1. Visual Studio で、作成、C#コンソール アプリ (**ファイル** > **新規** > **プロジェクト** > **Visual C#**   > **コンソール アプリケーション**) という名前の*ThrowsNullException*します。 Visual Studio でプロジェクトを作成する方法の詳細については、次を参照してください。[チュートリアル: 単純なアプリケーション作成](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)です。
   
1. Visual Studio でプロジェクトを開いたら、開く、 *Program.cs*ファイル。 Main() メソッドをコンソールには行を表示し、NullReferenceException をスローし、次のコードに置き換えます。
   
   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```
   
1. ソリューションをビルドするには、いずれかを選択、**デバッグ**(既定値) または**リリース**構成、および選択**ビルド** > **ソリューションのリビルド**. 
   
   >[!NOTE]
   >- 選択**デバッグ**完全なデバッグ エクスペリエンスを構成します。 
   >- 選択した場合[リリース](../debugger/how-to-set-debug-and-release-configurations.md)構成では、オフにする必要があります[マイ コードのみ](../debugger/just-my-code.md)この手順を実行します。 **ツール** > **オプション** > **デバッグ**、選択を解除**マイ コードのみを有効にする**します。
   ビルド構成の詳細については、次を参照してください。[ビルド構成について](../ide/understanding-build-configurations.md)します。
   
1. ビルドされたアプリを開いて*ThrowsNullException.exe*で、C#プロジェクト フォルダー (*...\ThrowsNullException\ThrowsNullException\bin\Debug*または *...\ThrowsNullException\ThrowsNullException\bin\Release*)。 
   
   次のコマンド ウィンドウが表示されます。
   
   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")
   
1. **Just-In-Time デバッガーの選択**ダイアログ ボックスが開きます。
   
   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")
   
   **使用可能なデバッガー**を選択します**の新しいインスタンス\<優先 Visual Studio のバージョン/エディション >** 選択されていない場合は、します。 
   
1. **[OK]** を選択します。
   
   ThrowsNullException プロジェクトが Visual Studio の新しいインスタンスで実行が例外をスローした行で停止します。
   
   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

この時点でのデバッグを開始することができます。 実際のアプリをデバッグしていた場合は、コードが例外をスローして理由を確認する必要があります。

> [!CAUTION]
> アプリに信頼できないコードが含まれている場合は、デバッグを開始するかどうかを決定する際に有効にすると、セキュリティ警告ダイアログ ボックスが表示されます。 デバッグを続行する前に、コードを信頼するかどうかを決定します。 このコードは、自分で作成したコードですか。 アプリケーションをリモート コンピューター上で実行している場合、プロセスの名前を識別できますか。 アプリはローカルで実行している場合は、コンピューターで実行されている悪意のあるコードの可能性を検討してください。 コードが信頼できる場合は、選択**OK**します。 それ以外の場合、**[キャンセル]** を選択します。

## <a name="jit_errors"></a> ジャスト イン タイムのトラブルシューティングのデバッグ 

ジャスト イン タイムの場合のデバッグが開始しませんアプリがクラッシュした場合でも、Visual Studio で有効になっています。

- Windows エラー報告は、コンピューターに処理エラーの上にしている可能性があります。 
  
  この問題を解決するには、レジストリ エディターを使用して、追加、 **DWORD 値**の**無効になっている**で**値データ**の**1**、次のレジストリ キーに。
  
  

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows エラーの報告**
    
  - (64 ビット コンピューター) 用: **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows エラーの報告**
  
  詳細については、次を参照してください。[します。WER 設定](https://docs.microsoft.com/windows/desktop/wer/wer-settings)します。
  
- Windows の既知の問題が原因で時間にのみデバッガーが失敗します。 
  
  修正を追加するには、 **DWORD 値**の**自動**で**値データ**の**1**、次のレジストリ キーに。
  
  
  - **Hkey_local_machine \software\microsoft\windows NT\CurrentVersion\AeDebug**
    
  - (64 ビット コンピューター) 用: **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

ジャスト イン タイムの中に次のエラー メッセージを表示する場合がありますのデバッグします。

- **クラッシュ プロセスにアタッチできません。指定したプログラムは、Windows または MS-DOS プログラムではできません。**

    デバッガーは、別のユーザーで実行されているプロセスにアタッチしようとしました。

    Visual Studio で、この問題を回避するには、開く**デバッグ** > **プロセスにアタッチ**、デバッグするプロセスを検索し、**選択可能なプロセス**リスト。 プロセスの名前がわからない場合にプロセス ID の検索、 **Visual Studio Just-In-Time デバッガー**ダイアログ。 プロセスの選択、**選択可能なプロセス**一覧**アタッチ**します。 選択**いいえ**Just ポイントイン タイムを消去するデバッガー ダイアログ。

- **ユーザーがログオンしていないために、デバッガーを開始できませんでした。**

    時刻でだけを表示するユーザーのセッションが存在しないために、コンソールにログオンしているユーザーがいないダイアログをデバッグします。

    この問題を解決するには、コンピューターにログオンします。

- **クラスが登録されていません。**

    デバッガーは、登録されていない、おそらくインストールの問題が原因 COM クラスを作成しようとしました。

    この問題を解決するには、再インストールするか、Visual Studio のインストールを修復する Visual Studio インストーラーを使用します。

## <a name="see-also"></a>関連項目
- [デバッガーのセキュリティ](../debugger/debugger-security.md)
- [デバッガーの基本事項](../debugger/getting-started-with-the-debugger.md)
- [オプション、デバッグ、ジャスト イン タイム ダイアログ ボックス](../debugger/just-in-time-debugging-options-dialog-box.md)
- [セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
