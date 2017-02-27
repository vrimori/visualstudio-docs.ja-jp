---
title: "チュートリアル: インストルメンテーションを使ったコマンド ライン プロファイリング | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロファイリング ツール、チュートリアル"
  - "パフォーマンス ツール、チュートリアル"
  - "パフォーマンス ツール、コマンド ライン ツール"
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# チュートリアル: インストルメンテーションを使ったコマンド ライン プロファイリング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のスタンドアロン アプリケーションのプロファイリングにより、プロファイリング ツールのインストルメンテーション メソッドを使用して、詳細なタイミング データおよび呼び出し数データを収集する方法を説明します。  このチュートリアルでは、次のタスクを行います。  
  
-   [VSInstr](../profiling/vsinstr.md) コマンド ライン ツールを使用して、インストルメント化されたバイナリを生成する。  
  
-   [VSPerfCLREnv](../profiling/vsperfclrenv.md) ツールを使用して .NET プロファイリング データを収集するように環境変数を設定する。  
  
-   [VSPerfCmd](../profiling/vsperfcmd.md) ツールを使用して、プロファイリング データを収集する。  
  
-   [VSPerfReport](../profiling/vsperfreport.md) ツールを使用して、プロファイリング データのファイル ベースのレポートを生成する。  
  
## 必須コンポーネント  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   C\# についての中級レベルの知識  
  
-   コマンド ライン ツールの操作についての中級レベルの知識  
  
-   [PeopleTrax サンプル](../profiling/peopletrax-sample-profiling-tools.md) のコピー  
  
-   プロファイリングによって得られた情報を操作するには、デバッグ シンボル情報を使用できるようにしておくことをお勧めします。  詳細については、「[方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)」を参照してください。  
  
## インストルメンテーション メソッドを使用したコマンド ライン プロファイリング  
 インストルメンテーションとは、1 つのプロファイリング方式です。インストルメントされるモジュール内の関数に制御が渡されるときと、関数から制御が返されるときのタイミング情報を収集するプローブ関数が、プロファイリングされるバイナリの特別に構築されたバージョンに含まれています。  このプロファイリング方式は、サンプリングよりも深くプログラムに入り込むので、オーバーヘッドが大きくなります。  インストルメントされたバイナリはデバッグまたはリリース バイナリよりも大きく、配置向けではありません。  
  
> [!NOTE]
>  インストルメントされたバイナリを顧客に配布することのないように注意してください。  インストルメントされたバイナリには、さまざまなリスクが存在します。  セキュリティ上のリスクはもちろん、バイナリに含まれる情報を基に、アプリケーションのリバース エンジニアリングを容易に行うことができてしまうという問題もあります。  
  
#### インストルメンテーション メソッドを使用して PeopleTrax アプリケーションのプロファイリングを行うには  
  
1.  PeopleTrax サンプル アプリケーションをインストールして、リリース バージョンをビルドします。  
  
2.  コマンド プロンプト ウィンドウを開いて、ローカル パス環境変数に**プロファイリング ツール** ディレクトリを追加します。  
  
3.  作業ディレクトリを PeopleTrax バイナリを含むディレクトリに変更します。  
  
4.  ファイル ベース レポートを含むディレクトリを作成します。  次のコマンドを入力します。  
  
    ```  
    md Reports  
    ```  
  
5.  VSInstr コマンド ライン ツールを使用して、アプリケーションにバイナリをインストルメント化します。  次のコマンドを別々のコマンド ラインに入力します。  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **注意** 既定では、インストルメントされていない元のファイルのバックアップが保存されます。  バックアップ ファイルの名前には、.orig という拡張子が付きます。  たとえば、元のバージョンの "MyApp.exe" は、"MyApp.exe.orig" として保存されます。  
  
6.  次のコマンドを入力し、適切な環境変数を設定します。  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  プロファイラーを起動するには、次のコマンドを入力します。  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  プロファイラーをトレース モードで開始すると、インストルメント化されたバージョンの PeopleTrax.exe プロセスによってデータが収集されます。  
  
     **PeopleTrax** アプリケーション ウィンドウが表示されます。  
  
9. **\[Get People\]** をクリックします。  
  
     PeopleTrax データ グリッドにデータが設定されます。  
  
10. **\[データのエクスポート\]** をクリックします。  
  
     メモ帳が開かれ、**PeopleTrax** アプリケーションの人名リストを含む新しいファイルが表示されます。  
  
11. メモ帳を閉じ、**PeopleTrax** アプリケーションを閉じます。  
  
12. プロファイラーをシャットダウンします。  次のコマンドを入力します。  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. 次のコマンドを入力し、環境変数をリセットします。  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. VSPerfReport ツールを使用してコンマ区切り値 \(csv\) レポート ファイルを生成します。  Type:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     スプレッドシート プログラムで生成されたレポートを分析できます。または、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE を使用して、Report.vsp ファイル内のプロファイリング データを分析することもできます。  詳細については、「[プロファイリング ツール データの分析](../profiling/analyzing-performance-tools-data.md)」を参照してください。  
  
## 参照  
 [パフォーマンス セッションの概要](../profiling/performance-session-overview.md)   
 [コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [サンプリング データ値について](../profiling/understanding-sampling-data-values.md)   
 [プロファイル ツールのレポート ビュー](../profiling/performance-report-views.md)