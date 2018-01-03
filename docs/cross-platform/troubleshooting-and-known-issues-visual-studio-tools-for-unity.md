---
title: "トラブルシューティングと既知の問題 (Visual Studio Tools for Unity) | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: "5"
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload: unity
ms.openlocfilehash: 7ede7734ec2a8c261cce3f31e06e77f932edd326
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>トラブルシューティングと既知の問題 (Visual Studio Tools for Unity)
このセクションには、Visual Studio Tools for Unity における一般的な問題の解決法、既知の問題についての説明、およびエラー報告によって Visual Studio Tools for Unity を改善する方法について記されています。  

## <a name="troubleshooting"></a>トラブルシューティング  
Visual Studio Tools for Unity の一般的な問題を解決するには、以下のセクションを参照してください。  

### <a name="visual-studio-crashes"></a>Visual Studio がクラッシュする
Visual Studio MEF キャッシュの破損が原因になっている可能性があります。

MEF キャッシュをリセットするには、次のフォルダーを削除する必要があります (これを行う前に、Visual Studio を終了してください)。

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

これで問題は解決するはずです。 まだ問題が発生する場合は、管理者として Visual Studio の開発者コマンド プロンプトを実行し、次のコマンドを使います。

```batch
 devenv /setup
```

### <a name="issues-with-vs2015-and-intellisense-or-code-coloration"></a>VS2015 および Intellisense またはコード配色の問題
Visual Studio 2015 を Update 3 にアップグレードする必要があります。

### <a name="visual-studio-hangs"></a>Visual Studio がハングする
Parse、FMOD、UMP (Universal Media Player)、ZFBrowser、Embedded Browser などの複数の Unity プラグインは、ネイティブ スレッドを使っています。 これは、プラグインがランタイムへのネイティブ スレッドのアタッチを終了した後で OS への呼び出しをブロックしている問題です。 つまり、Unity はデバッガー (またはドメインの再読み込み) のためにスレッドを中断できずにハングします。

FMOD の場合は回避策があります。FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE 初期化[フラグ](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html)を渡して非同期処理を無効にし、メイン スレッドですべての処理を実行します。

### <a name="incompatible-project-in-visual-studio"></a>Visual Studio での互換性のないプロジェクト
最初に、Unity で Visual Studio が外部スクリプト エディターとして設定されていることを確認します ([編集]/[環境設定]/[外部ツール])。 次に、Visual Studio プラグインが Unity にインストールされていることを確認します ([ヘルプ]/[バージョン情報] で、"Microsoft Visual Studio Tools for Unity is enabled" (Microsoft Visual Studio Tools for Unity が有効になっています) のようなメッセージが下部に表示される必要があります)。 さらに、拡張機能が Visual Studio に正しくインストールされていることを確認します ([ヘルプ]/[バージョン情報])。

### <a name="assembly-reference-issues"></a>アセンブリ参照の問題
プロジェクトの参照が複雑な場合、またはこの生成ステップをいっそう適切に制御したい場合は、[API](../cross-platform/customize-project-files-created-by-vstu.md) を使って、生成されるプロジェクトまたはソリューションのコンテンツを操作できます。 また、Unity プロジェクトで[応答ファイル](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)を使って処理を任せることもできます。

### <a name="breakpoints-with-a-warning"></a>ブレークポイントでの警告
Visual Studio が特定のブレークポイントのソースの場所を見つけられない場合、ブレークポイントの周囲に警告が表示されます。 使っている動作が現在の Unity シーンに正しく読み込まれて使われていることを確認してください。

### <a name="breakpoints-not-hit"></a>ブレークポイントがヒットない
 使っている動作が現在の Unity シーンに正しく読み込まれて使われていることを確認してください。 Visual Studio と Unity の両方を終了し、すべての生成されたファイル (*.csproj、*.sln) と Library フォルダー全体を削除します。

### <a name="unable-to-attach"></a>アタッチできない
-   ウイルス対策ソフトウェアを一時的に無効にするか、VS と Unity 両方に対する除外規則を作成してみてください。
-   ファイアウォールを一時的に無効にするか、VS と Unity の間の TCP/UDP ネットワークを許可する規則を作成してみてください。
-   Team Viewer などのプログラムがプロセスの検出を妨げることがわかっています。余分なソフトウェアを一時的に停止して、何か変わるかを確認してみてください。
-   VSTU は "Unity.exe" プロセスを監視するだけなので、メインの Unity 実行可能ファイルの名前を変更しないでください。

### <a name="unable-to-debug-android-players"></a>Android プレーヤーをデバッグできない
プレーヤーの検出にはマルチキャストが使われていますが (Unity で使われる既定のメカニズム)、その後で通常の TCP 接続を使ってデバッガーをアタッチします。 検出フェーズが Android デバイスの主な問題です。

USB はデバッグに関しては超高速ですが、Unity プレーヤーの検出メカニズムと互換性がありません。
Wi-Fi は高い汎用性を備えていますが、待機時間のため USB と比べると非常に低速です。 一部のルーターまたはデバイス (よく知られているのは Nexus シリーズ) では、マルチキャストが適切にサポートされていないことがわかっています。

USB を使って以下を試し、接続されたデバイスで開かれているポートを確認できます (デバッグ ポート (常に 56xxx の形式) を認識できるように、プレーヤーを稼働状態にします)。

```shell  
adb shell netstat
```  

ローカル PC にポートを転送します。

```shell  
adb forward tcp:56xxx tcp:56xxx
```  

その後、転送されたポート 127.0.0.1:56xxx を使って VSTU を接続します。

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>UnityVS から UnityVS to Visual Studio Tools for Unity への移行  
 UnityVS から Visual Studio Tools for Unity に移行している場合、Unity プロジェクト用の新しい Visual Studio ソリューションを生成する必要があります。  

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Unity プロジェクトを UnityVS 1.8 から Visual Studio Tools for Unity 1.9 に移行する方法  

1.  古いソリューションとプロジェクト ファイルを Unity プロジェクトから削除します。 Unity プロジェクトのルート ディレクトリで、Visual Studio .sln と *proj ファイルを見つけてすべて削除します。  

2.  Visual Studio Tools for Unity パッケージを Unity プロジェクトにインポートします。 VSTU パッケージをインポートする方法については、「 [作業の開始](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) 」ページの「Visual Studio Tools for Unity の構成」をご覧ください。  

3.  新しいソリューションとプロジェクト ファイルを生成します。 今すぐに作成する場合は、Unity エディターのメイン メニューで、**[Visual Studio Tools]**、**[Generate Project Files]** を選択します。 あるいは、この手順をスキップすることもできます。その場合、**[Visual Studio Tools]**、**[Open in Visual Studio]** と選択すると新しいファイルが自動的に Visual Studio Tools for Unity によって作成されます。  

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows の場合に Unity ターゲット フレームワークをダウンロードするよう Visual Studio から求められる  
 Visual Studio Tools for Unity には .NET Framework 3.5 が必要ですが、Windows 8 または 10 では既定でインストールされません。 この問題を解決するには、.NET Framework 3.5 のダウンロードとインストールに関する手順に従ってください。  

## <a name="known-issues"></a>既知の問題  
 デバッガーが Unity の古いバージョンの C# コンパイラとやり取りする方法に起因する、Visual Studio Tools for Unity の既知の問題があります。 これらの問題を修正するために作業中ですが、修正されるまでは以下の問題が発生する可能性があります。  

-   デバッグ時に Unity がクラッシュすることがあります。  

-   デバッグ時に Unity がフリーズすることがあります。  

-   メソッドのステップインとステップアウトが正しく動作しないことがあります。特に、反復子または switch ステートメント内でこれが生じる可能性があります。  

## <a name="reporting-errors"></a>エラーの報告  
 クラッシュ、フリーズ、またはその他のエラーが発生する場合、エラー レポートを送信することによって、Visual Studio Tools for Unity の品質向上にご協力ください。 Visual Studio Tools for Unity における問題の調査と解決に役立ちます。 ご協力に感謝いたします。  

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio がフリーズする場合にエラーを報告する方法  
 Visual Studio Tools for Unity でデバッグすると Visual Studio がフリーズするという報告を受け取っていますが、問題を把握するためにさらにデータを必要としています。 次の手順を実行していただくと、調査に役立ちます。  

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity でデバッグすると Visual Studio がフリーズすることを報告する方法

*Windows の場合:*  

1.  Visual Studio の新しいインスタンスを開きます。

2.  [プロセスにアタッチ] ダイアログ ボックスを開きます。 Visual Studio の新しいインスタンスのメイン メニューで、**[デバッグ]**、**[プロセスにアタッチ]** を選択します。  

3.  Visual Studio のフリーズしたインスタンスに、デバッガーをアタッチします。 **[プロセスにアタッチ]** ダイアログ ボックスで、**[選択可能なプロセス]** テーブルからフリーズした Visual Studio インスタンスを選択し、**[アタッチ]** ボタンを選択します。  

4.  デバッガーを一時停止します。 Visual Studio の新しいインスタンスのメイン メニューで **[デバッグ]**、**[すべて中断]** を選ぶか、単に **Ctrl + Alt + Break** キーを押します。  

5.  スレッド ダンプを作成します。 コマンド ウィンドウで、次のコマンドを入力して **Enter** キーを押します。  

    ```powershell  
    Debug.ListCallStack /AllThreads /ShowExternalCode  
    ```  

    最初に **[コマンド]** ウィンドウを表示しなければならない場合もあります。 Visual Studio のメイン メニューで、**[ビュー]**、**[その他のウィンドウ]**、**[コマンド ウィンドウ]** の順に選択します。  

*Mac の場合:*

1. 端末を開き、Visual Studio for Mac の PID を取得します。

    ```shell  
    ps aux | grep "[V]isual Studio.app"
    ```

1. lldb デバッガーを起動します。

    ```shell  
    lldb
    ```

1. PID を使って Visual Studio for Mac のインスタンスにアタッチします。

    ```shell  
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. すべてのスレッドの StackTrace を取得します。

    ```shell  
    bt all
    ```

最後に、Visual Studio がフリーズ状態になったときに実行していた作業内容に関する説明を添えて、スレッド ダンプを [vstusp@microsoft.com](mailto:vstusp@microsoft.com)に送信します。
