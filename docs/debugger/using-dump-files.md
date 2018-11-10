---
title: Visual Studio デバッガーでのダンプ ファイルを使用して、|Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 11/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74935071dcba3ab145f17f594fd22491271e39c6
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296139"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Visual Studio デバッガーでのダンプ ファイル

<a name="BKMK_What_is_a_dump_file_"></a> A*ダンプ ファイル*プロセスが実行していると、ポイントでアプリのために読み込まれたモジュールに表示されるスナップショットです。 ヒープ情報ありのダンプも、アプリのメモリのスナップショットをその時点であります。 

Visual Studio でのヒープ ダンプ ファイルを開くと、デバッグ セッションで、ブレークポイントで停止するようなものです。 実行を継続することはできませんが、ダンプの時にスタック、スレッド、およびアプリの変数の値を確認できます。

ダンプは主に開発者がアクセスできないコンピューターからの問題のデバッグに使用されます。 自分のコンピューターでハングまたはクラッシュを再現できない場合は、お客様のコンピューターからのダンプ ファイルを使用できます。 テスト担当者は、クラッシュを保存したりより多くのテストを使用するデータのハング ダンプも作成します。 

Visual Studio デバッガーでは、マネージドまたはネイティブ コードのダンプ ファイルを保存できます。 内のファイルを保存する他のアプリまたは Visual Studio によって作成されたダンプ ファイルをデバッグできる、*ミニダンプ*形式。

##  <a name="BKMK_Requirements_and_limitations"></a> 要件と制限事項

-   64 ビット コンピューターからのダンプ ファイルをデバッグするには、64 ビット コンピューターで Visual Studio を実行する必要があります。

-   Visual Studio では、ARM デバイスからのネイティブ アプリのダンプ ファイルをデバッグできます。 ネイティブ デバッガーでのみが、ARM デバイスから管理対象アプリのダンプ デバッグすることもできます。

-   デバッグする[カーネル モード](/windows-hardware/drivers/debugger/kernel-mode-dump-files)ダンプ ファイル、またはを使用して、 [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension)で Windows 用デバッグ ツールをダウンロードする Visual Studio で、拡張機能のデバッグ、 [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk)します。

-   Visual Studio は、旧バージョンの保存されたダンプ ファイルをデバッグできません[フル ユーザー モード ダンプ](/windows/desktop/wer/collecting-user-mode-dumps)形式。 フル ユーザー モード ダンプがヒープ ダンプとされません。

-   最適化されたコードのダンプ ファイルをデバッグすると、混乱が生じることがあります。 たとえば、コンパイラが関数のインライン展開により予期しない呼び出しスタックとその他の最適化は、変数の有効期間が変更される可能性が。

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> またはヒープなしのダンプ ファイル

ダンプ ファイルは、可能性がありますか、ヒープ情報がない可能性があります。

-   **ダンプ ファイルがヒープ情報あり**ダンプの時に、変数の値を含む、アプリのメモリのスナップショットが含まれます。 Visual Studio には、非常に簡単にデバッグを行い、ヒープを使用して、ダンプ ファイルに読み込まれたネイティブ モジュールのバイナリも保存します。 Visual Studio は、バイナリ、アプリを見つけられない場合でも、ヒープを使用してダンプ ファイルからシンボルを読み込むことができます。 

-   **ヒープなしのダンプ ファイル**ヒープ情報あり、ダンプよりかなり小さくなりますが、デバッガーがシンボル情報を検索するアプリのバイナリを読み込む必要がありますが、します。 読み込まれたバイナリはダンプの作成時に実行されているものと正確に一致する必要があります。 ヒープなしのダンプ ファイルは、スタック変数のみの値を保存します。

##  <a name="BKMK_Create_a_dump_file"></a> ダンプ ファイルを作成します。

Visual Studio でのプロセスをデバッグするときに、例外またはブレークポイントでデバッガーが停止したときにダンプを保存できます。 

[Just-In-Time デバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)有効にすると、Visual Studio の外部でクラッシュしたプロセスに Visual Studio デバッガーをアタッチし、デバッガーからダンプ ファイルを保存します。 参照してください[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。

**ダンプ ファイルを保存します。**

1. デバッグ中に、エラーまたはブレークポイントで停止すると、選択**デバッグ** > **ダンプを保存**します。 

1. **ダンプを保存**ダイアログ ボックスで、**型として保存**を選択します**ミニダンプ**または**ヒープ付きミニダンプ**(既定)。

1. パスを参照し、ダンプ ファイルの名前を選択し、**保存**します。 

>[!NOTE]
>Windows ミニダンプ形式をサポートする任意のプログラムでは、ダンプ ファイルを作成できます。 たとえば、 **Procdump**コマンド ライン ユーティリティから[Windows Sysinternals](http://technet.microsoft.com/sysinternals/default)ベースのトリガーまたは必要に応じて、プロセスのクラッシュ ダンプ ファイルを作成できます。 参照してください[要件と制限事項](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations)については、その他のツールを使用して、ダンプ ファイルを作成する方法。

##  <a name="BKMK_Open_a_dump_file"></a> ダンプ ファイルを開く

1. Visual Studio で、次のように選択します。**ファイル** > **オープン** > **ファイル**します。

1. **ファイルを開く** ダイアログ ボックスを検索して、ダンプ ファイルを選択します。 通常は必要があります、 *.dmp*拡張機能。 **[OK]** を選択します。

   **ミニダンプ ファイル概要**ウィンドウ表示の概要とモジュールに関する情報のダンプ ファイル、およびアクションを実行できます。

   ![ミニダンプ概要ページ](../debugger/media/dbg_dump_summarypage.png "ミニダンプ概要ページ")

1. **アクション**:
   - シンボルの読み込み場所を設定する選択**シンボル パスの設定**します。
   - デバッグを開始する次のように選択します。**管理のみでデバッグ**、**ネイティブのみでデバッグ**、**混合でデバッグ**、または**マネージ メモリの使用をデバッグ**します。

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> .Exe、.pdb、およびソース ファイルを検索します。

使用するには、完全なデバッグ機能、ダンプ ファイルを Visual Studio が必要です。

- *.Exe*ダンプが作成されたファイルとその他のバイナリ (Dll など)、ダンプ プロセスを使用します。
- シンボル (*.pdb*) 用のファイル、 *.exe*およびその他のバイナリです。
- *.Exe*と *.pdb*バージョンと、このファイルのビルドに正確に一致するファイルの作成をダンプします。
- 関連するモジュールのソース ファイル。 ソース ファイルが見つからない場合は、モジュールの逆アセンブリを使用できます。

ダンプにヒープ データがある場合は、Visual Studio は、一部のモジュールでは、不足しているバイナリを扱うことができますが、有効な呼び出し履歴を生成するための十分なモジュールのバイナリが必要になります。 

### <a name="search-paths-for-exe-files"></a>.Exe ファイルの検索パス

Visual Studio は、これらの場所を自動的に検索 *.exe*ダンプ ファイルに含まれていないファイル。

1. ダンプ ファイルを格納するフォルダー。
2. ダンプ ファイルを指定します、ダンプを収集するコンピューター上のモジュール パスは、モジュールのパス。
3. 指定されたシンボル パス**ツール**(または**デバッグ**) >**オプション** > **デバッグ** >  **シンボル**します。 開くことも、**シンボル**ページから、**アクション**のウィンドウ、**ダンプ ファイルの概要**ウィンドウ。 このページで、検索する複数の場所を追加できます。

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>No バイナリ、No の記号、またはソースが見つかりませんページを使用してください。

Visual Studio は、ファイルを見つけられない場合に、ダンプのモジュールをデバッグする必要がある、表示、**バイナリが見つかりません**、**シンボルが見つかりません**、または**ソースが見つかりません**ページ。 これらのページは、問題の原因に関する詳細情報を提供し、ファイルを検索するのに役立つアクション リンクを提供します。 参照してください[シンボル (.pdb) ファイルとソース ファイルを指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)します。

## <a name="see-also"></a>関連項目

- [ジャストイン タイムのデバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)
- [シンボル (.pdb) ファイルとソース ファイルを指定します。](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)