---
title: "方法: LocalDB にアップロードするか、SQL Server Express の使用を続行する | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "LocalDB"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQLEXPRESS"
  - "アップグレード (SQLExpress に)"
  - "アップグレード (LocalDB に)"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法: LocalDB にアップロードするか、SQL Server Express の使用を続行する
このトピックでは [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 説明をインストールし、次のタスクの順序がと、データベース ファイル \(.mdf\) をアップグレードするためのオプションを:  
  
-   LocalDB を使用するデータベースをアップグレードします。  
  
-   SQL Server Express の新しいバージョンを使用するようにデータベース ファイルをアップグレードします。  
  
-   [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] のデータベース ファイルを使用しますが、[!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]の互換性を保持します。  
  
-   SQL Server Express に既定のデータベース エンジンを実行します。  
  
 SQL Server Express の古いバージョンを使用して作成されたデータベース ファイル \(.mdf\) を含むプロジェクトを開くために [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] を使用できます。  ただし、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]のプロジェクトを開発し続けるように、または同じにインストールされている SQL Server Express のバージョンが Visual Studio としてコンピューターを使用、または SQL Server Express データベース ファイルに LocalDB をアップグレードする必要があります。必要があります。  データベース ファイルをアップグレードする場合、SQL Server Express の古いバージョンにアクセスします。  
  
 また [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] を使用してファイルのバージョンが現在インストールされている SQL Server Express のインスタンスとの互換性がある作成したデータベース ファイルをアップグレードするように要求できます。  問題を解決するには、Visual Studio は、SQL Server Express の新しいバージョンにファイルをアップグレードするように求めるメッセージが表示されます。  
  
> [!IMPORTANT]
>  ここでは、アップグレードする前にデータベースをバックアップすることをお勧めします。  
  
 データベースをアップグレードする前に、次の条件を考慮する必要があります:  
  
-   [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] と [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]両方のプロジェクトに使用する場合は、アップグレードしないでください。  
  
-   アプリケーションが LocalDB ではなく SQL Server Express を使用する環境で使用される向上します。  
  
-   LocalDB がそれらをサポートしないため、アプリケーションがリモート接続を使用して向上します。  
  
-   アプリケーションが Internet Information Services \(IIS\) に依存していた場合です向上します。  
  
-   サンドボックスの環境でデータベース アプリケーションをテストする必要があるが、データベースを管理するようにアップグレードすることを検討してください。  
  
### データベース ファイルを LocalDB を使用するようにアップグレードするには  
  
1.  **\[サーバー エクスプローラー\]**では、**\[データベースへの接続\]** のボタンをクリックします。  
  
2.  **\[接続の追加\]** のダイアログ ボックスで、次の情報を指定する:  
  
    -   **データ ソース:** Microsoft SQL Server \(SqlClient\)  
  
    -   **サーバー名:** \(LocalDB\) \\v11.0  
  
    -   *\[パス\]* が主要 .mdf ファイルの物理パスです**データベース ファイルを添付する:**、*\[パス\]*。  
  
    -   *\[名前\]* が、ファイルで使用する名前です。**論理名:**、*\[名前\]*。  
  
3.  **\[OK\]** を選択します。  
  
4.  メッセージが表示されたら、ファイルをアップグレードするに **あり** のボタンをクリックします。  
  
 データベースは LocalDB のデータベース エンジンにアタッチされて、その [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]と互換性のあるアップグレードしない。  
  
 また、開いて、**\[接続の変更\]**接続を選択することによって LocalDB をショートカット メニューを使用するに SQLExpress の接続を変更できます。  **\[接続の変更\]** のダイアログ ボックスで、LocalDB \(\) \\v11.0 にサーバー名を変更します。  **\[詳細プロパティ\]** のダイアログ ボックスで、**ユーザー インスタンス** が false に設定されていることを確認します。  
  
### SQL Server Express の新しいバージョンにアップグレードします。  
  
1.  データベースへの接続のショートカット メニューで、**\[接続の変更\]**を選択します。  
  
2.  **\[接続の変更\]** のダイアログ ボックスで、**\[詳細設定\]** のボタンをクリックします。  
  
3.  **\[詳細プロパティ\]** のダイアログ ボックスで、サーバー名を変更せずに **\[OK\]** のボタンをクリックします。  
  
 データベース ファイルは [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)]の現在のバージョンに一致するようにアップグレードされます。  
  
### [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] のデータベースを使用するには、[!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]の互換性を保持する  
  
1.  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]では、アップグレードせずにプロジェクトを開きます。  
  
    -   プロジェクトを実行するには、F5 キーを選択します。  
  
    -   、[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]で行ったように、データベースを編集するには、**\[ソリューション エクスプローラー\]**の .mdf ファイルを開き、データベースを使用するに **\[サーバー エクスプローラー\]** のノードを展開します。  
  
### SQL Server Express に既定のデータベース エンジンをするには  
  
1.  メニュー バーで、**\[ツール\]**、**\[オプション\]**を選択します。  
  
2.  **\[オプション\]** のダイアログ ボックスで、**\[データ ツール\]** の選択を展開し、**\[データ接続\]** のノードを選択します。  
  
3.  **\[SQL Server のインスタンス名\]** のテキスト ボックスで、使用する SQL Server Express のインスタンスの名前を指定します。  インスタンスが示されなかったら、`。\SQLEXPRESS`を指定します。  
  
4.  **\[OK\]** を選択します。  
  
 SQL Server Express は、アプリケーションの既定のデータベース エンジンです。  
  
## 参照  
 [ローカル データの概要](../data-tools/local-data-overview.md)   
 [チュートリアル: ローカル データベース ファイル内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)