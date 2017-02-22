---
title: "方法 : スタンドアロンのプロファイラーをインストールする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パフォーマンス ツール, インストール (スタンドアロンのプロファイラーを)"
  - "プロファイル ツール, スタンドアロンのプロファイラー"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : スタンドアロンのプロファイラーをインストールする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] には、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE をインストールせずに実行できるスタンドアロンのプロファイラーに基づいたコマンド ラインが用意されています。  この状況は、コンピューターに開発環境をインストールしていない場合またはインストールできない場合に発生します。  たとえば、運用 Web サーバーには開発環境をインストールしません。  
  
> [!NOTE]
>  スタンドアロン プロファイラーを使用して ASP.NET Web サイトのパフォーマンス データを収集する場合は、[VSPerfCmd](../profiling/vsperfcmd.md) ツールより [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) ツールが推奨されます。  
  
### スタンドアロンのプロファイラーをインストールするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インストール メディアの \\Standalone Profiler というパスを含むディレクトリで、スタンドアロンのプロファイラーのインストーラー \(vs\_profiler.exe\) を探して実行します。  
  
2.  vsintr.exe および msdis150.dll のパスをシステム パスに追加します。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の既定のインストールでは、vsinstr.exe および msdis150.dll は \\Program Files\\Visual Studio 10\\Team Tools\\Performance Tools にあります。  
  
3.  コマンド プロンプトで、「**VSInstr**」と入力します。  
  
    > [!NOTE]
    >  vsinstr.exe の使用方法が表示される場合は、すべてが正しく設定されています。  vsinstr.exe またはその依存関係の 1 つが見つからないことを示すエラーが発生した場合は、手順 2. で説明したように、パスを正しく設定したことを確認してください。  
  
4.  **\_NT\_SYMBOL\_PATH** 変数に **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols** を設定して、シンボル サーバーを設定します。  
  
5.  システム環境変数を使用してシンボル サーバーをセットアップした後、新しいコマンド プロンプトで、コマンド ライン プロファイラー ツールを実行します。  これにより、新しい環境変数が有効になります。  コマンド プロンプト ウィンドウで、次のコマンドを入力します。  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  シンボル サーバー パッケージのセットアップ方法の詳細な手順については、「[方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)」を参照してください。  
  
6.  [VSPerfReport](../profiling/vsperfreport.md) ツールを使用して、シンボルをプロファイリング データ \(.vsp\) ファイルにシリアル化します。  **VSPerfReport \/summary:all \/packsymbols** スイッチを使用します。  データ ファイルにシンボルが挿入されていない場合は、\_NT\_SYMBOL\_PATH 環境変数を設定したことを確認します。  
  
## 参照  
 [コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [チュートリアル: サンプリングを使ったコマンド ライン プロファイリング](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)   
 [チュートリアル: インストルメンテーションを使ったコマンド ライン プロファイリング](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)