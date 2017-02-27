---
title: "VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロファイリング ツール、VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VSPerfASPNETCmd** コマンド ライン ツールを使用すると、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションのプロファイリングを簡単に行うことができます。  [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールに比べて、オプションが削減され、環境変数を設定する必要がなく、コンピューターの再起動も必要ありません。  スタンドアロン プロファイラーでプロファイリングを行う場合は、**VSPerfASPNETCmd** の使用をお勧めします。  詳細については、「[方法 : スタンドアロンのプロファイラーをインストールする](../profiling/how-to-install-the-stand-alone-profiler.md)」を参照してください。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。  Windows ストア アプリにも新しい収集手法が必要です。  「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
 同時実行データの収集やプロファイリングの一時停止と再開などの一部のシナリオでは、プロファイリングに **VSPerfCmd** の使用をお勧めします。  
  
> [!NOTE]
>  プロファイリング ツールのコマンド ライン ツールは、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] インストール ディレクトリの \\Team Tools\\Performance Tools サブディレクトリにあります。  64 ビット コンピューターでは、32 ビットの \\Team Tools\\Performance Tools ディレクトリにある VSPerfASPNETCmd ツールを使用します。  プロファイラー コマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。  詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。  
  
## ASP.NET アプリケーションをプロファイルする  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションをプロファイルするには、次の各セクションで説明するコマンドの 1 つを入力します。  Web サイトが起動し、プロファイラーが起動してデータを収集します。  アプリケーションを実行して、ブラウザーを閉じます。  プロファイリングを停止するには、コマンド プロンプト ウィンドウで Enter キーを押します。  
  
> [!NOTE]
>  既定では、**vsperfaspnetcmd** コマンドの後にコマンド プロンプトから制御は戻りません。  **\/nowait** オプションを使用すると、コマンド プロンプトから強制的に制御を戻すことができます。  [/NoWait オプションの使用](#UsingNoWait)を参照してください。  
  
## サンプリング メソッドを使用してアプリケーションの統計情報を収集するには  
 サンプリングは **VSPerfASPNETCmd** ツールの既定のプロファイル方法であるため、コマンド ラインで指定する必要はありません。  次のコマンド ラインは、指定した Web アプリケーションからアプリケーションの統計情報を収集します。  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## インストルメンテーション メソッドを使用して詳細なタイミング データを収集するには  
 次のコマンド ラインを使用して、動的にコンパイルされた [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションから詳細なタイミング データを収集します。  
  
 **vsperfaspnetcmd \/trace**  *websiteUrl*  
  
 Web アプリケーション内の静的にコンパイルされた .dll ファイルをプロファイリングする場合は、[VSInstr](../profiling/vsinstr.md) コマンド ライン ツールを使用してファイルをインストルメントする必要があります。  vsperfaspnetcmd \/trace コマンドを実行すると、インストルメント化されたファイルのデータが収集されます。  
  
## .NET メモリ データを収集するには  
 **\/Memory** オプションを使用すると、.NET メモリ内のオブジェクトの割り当てに関するデータが収集されるため、これらのオブジェクトの有効期間に関するデータを収集できます。  割り当てデータの収集は **\/Memory** データ オプションの既定のモードとして実行されるため、コマンド ラインで指定する必要はありません。  
  
 **vsperfaspnetcmd \/memory** *websiteUrl*  
  
 **Lifetime** パラメーターを使用して、割り当てデータに加え、オブジェクトの有効期間データを収集します。  
  
 **vsperfaspnetcmd \/memory:lifetime** *websiteUrl*  
  
 また、**\/Trace** オプションを使用して .NET メモリ データと共に詳細なタイミング情報を収集することもできます。  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/trace** `websiteUrl`  
  
## 階層相互作用データを収集するには  
  
> [!WARNING]
>  階層の相互作用のプロファイル \(TIP\) のデータは、[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)][!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、または [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]を使用して収集できます。  ただし、階層相互作用プロファイル データを表示できるのは、[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] および [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] のみです。  
>   
>  Windows 8 または Windows Server 2012 のヒント データを収集するには、インストルメンテーション \(**\/trace**\) オプションを使用する必要があります。  
  
 サンプリング データと共に階層相互作用データを収集するには、コマンド ラインに次のように入力します。  
  
 **vsperfaspnetcmd \/tip** `websiteUrl`  
  
 インストルメンテーション データと共に階層相互作用データを収集するには、コマンド ラインに次のように入力します。  
  
 **vsperfaspnetcmd \/trace \/tip** *websiteUrl*  
  
 .NET メモリ データと共に階層相互作用データを収集するには、コマンド ラインに次のように入力します。  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/tip** *websiteUrl*  
  
##  <a name="UsingNoWait"></a> \/NoWait オプションの使用  
 既定では、**vsperfaspnetcmd** コマンドの後にコマンド プロンプトから制御は戻りません。  次の構文オプションを使用すると、コマンド プロンプトから強制的に制御を戻すことができます。  その後、コマンド プロンプト ウィンドウで他の操作を実行できます。  プロファイリングを終了するには、別の **vsperfaspnetcmd** コマンドで **\/shutdown** オプションを使用します。  
  
 プロファイリングを開始するには、コマンド ラインに次のように入力します。  
  
 **vsperfaspnetcmd** \[*\/Options*\] **\/nowait** *websiteUrl*  
  
 プロファイリングを終了するには、コマンド ラインに次のように入力します。  
  
 **vsperfaspnetcmd \/shutdown** *websiteUrl*  
  
## 追加のオプション  
 **vsperfaspnetcmd \/shutdown** コマンドを除き、このセクションの前半で説明した各コマンドに次の任意のオプションを追加できます。  
  
|オプション|説明|  
|-----------|--------|  
|**\/Output:** `VspFile`|既定では、プロファイル データ \(.vsp\) ファイルは **PerformanceReport.vsp** というファイル名で現在のディレクトリに作成されます。  別の場所、ファイル名、またはその両方を指定するには、\/output オプションを使用します。|  
|**\/PackSymbols:Off**|既定では、VsPerfASPNETCmd に .vsp ファイルのシンボル \(関数、パラメーター名など\) が埋め込まれています。  シンボルを埋め込むと、プロファイル データ ファイルが非常に大きくなる可能性があります。  データを分析するときにシンボルが含まれた .pdb ファイルにアクセスする場合は、\/packsymbols:off オプションを使用してシンボルの埋め込みを無効にしてください。|