---
title: .Mdf ファイルをアップグレード |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 91a58a3605873f309b44f3d22ef4fbc2ca8c12f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="upgrade-mdf-files"></a>.Mdf ファイルをアップグレードします。

このトピックでは、新しいバージョンの Visual Studio をインストールした後、データベース ファイル (.mdf) をアップグレードするためのオプションについて説明します。 次のタスクの手順が含まれています。

- 新しいバージョンの SQL Server Express LocalDB を使用するデータベース ファイルをアップグレードします。

- SQL Server Express の新しいバージョンを使用するデータベース ファイルをアップグレードします。

- Visual Studio でのデータベース ファイルと連携しますが、古いバージョンの SQL Server Express または LocalDB との互換性を保持します。

- 既定のデータベース エンジンを SQL Server Express を行う

Visual Studio を使用すると、古いバージョンの SQL Server Express または LocalDB を使用して作成されたデータベース ファイル (.mdf) を含むプロジェクトを開きます。 ただし、Visual Studio でプロジェクトの開発を続行するには、そのバージョンの SQL Server Express または LocalDB は、Visual Studio と同じコンピューターにインストールされているであるか、データベース ファイルをアップグレードする必要があります。 データベース ファイルをアップグレードする場合は、古いバージョンの SQL Server Express または LocalDB を使用してアクセスできません。

また、ファイルのバージョンが SQL Server Express または現在インストールされている LocalDB のインスタンスと互換性がない場合は、SQL Server Express または LocalDB の以前のバージョンで作成されたデータベース ファイルをアップグレードするように求め可能性があります。 この問題を解決するには、Visual Studio は、ファイルをアップグレードすることを求められます。

> [!IMPORTANT]
> アップグレードする前に、データベース ファイルをバックアップすることをお勧めします。

> [!WARNING]
> LocalDB 2014 (V12) LocalDB 2016 (V13) を 32 ビットまたはそれ以降に作成された .mdf ファイルをアップグレードする場合、32 ビット バージョンの LocalDB でファイルをもう一度開くことはできません。

データベースをアップグレードする前に、次の条件を考慮してください。
  
-   以前のバージョンと新しいバージョンの Visual Studio の両方で、プロジェクトで作業する場合、アップグレードしません。  
  
-   代わりに使用する SQL Server Express LocalDB の環境でアプリケーションを使用する場合、アップグレードしません。  
  
-   LocalDB が受理しないために、アプリケーションは、リモート接続を使用する場合にアップグレードしません。  
  
-   アプリケーションには、インターネット インフォメーション サービス (IIS) が依存している場合、アップグレードしません。  
  
-   サンド ボックス環境でのデータベース アプリケーションをテストするたくないデータベースを管理する場合は、アップグレードを検討します。  
  
### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>LocalDB のバージョンを使用するデータベース ファイルをアップグレードするには
  
1.  **サーバー エクスプ ローラー**、select、**データベースへの接続**ボタンをクリックします。  
  
2.  **接続の追加** ダイアログ ボックスで、次の情報を指定します。  
  
    -   **データ ソース**: `Microsoft SQL Server (SqlClient)`  
  
    -   **サーバー名**:  
  
        -   既定のバージョンを使用する:`(localdb)\MSSQLLocalDB`です。  これは、指定 ProjectV12 または ProjectV13 のいずれかによって、どのバージョンの Visual Studio がインストールされているし、最初の LocalDB インスタンスの作成時にします。 **MSSQLLocalDB**内のノード**SQL Server オブジェクト エクスプ ローラー**ポイントをどのバージョンを示しています。  
  
        -   特定のバージョンを使用する:`(localdb)\ProjectsV12`または`(localdb)\ProjectsV13`V12 は LocalDB 2014、V13、LocalDB 2016。  
  
    -   **データベース ファイルを添付**: プライマリ .mdf ファイルの物理パス。  
  
    -   **論理名**: とファイルを使用する名前。  
  
3.  **[OK]** ボタンを選択します。  
  
4.  メッセージが表示されたら、選択、**はい**ファイルをアップグレードするボタンをクリックします。  
  
    データベースをアップグレードするには、LocalDB データベース エンジンに接続されておよび LocalDB の古いバージョンと互換性がありません。  
  
SQL Server Express を接続のショートカット メニューを開きを選択し、LocalDB を使用する接続を変更することもできます。**接続の変更**です。 **接続の変更** ダイアログ ボックスで、サーバーの名前を変更`(LocalDB)\MSSQLLocalDB`です。 **プロパティの詳細** ダイアログ ボックスで、ことを確認して**ユーザー インスタンス**に設定されている**False**です。

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>SQL Server Express のバージョンを使用するデータベース ファイルをアップグレードするには  
  
1.  ショートカット メニューで、データベースへの接続に、次のように選択します。**接続の変更**です。  
  
2.  **接続の変更**ダイアログ ボックスで、**詳細**ボタンをクリックします。  
  
3.  **プロパティの詳細**ダイアログ ボックスで、 **OK**サーバー名を変更することがなくボタンをクリックします。  
  
    データベース ファイルは、SQL Server Express の現在のバージョンを一致するようにアップグレードします。  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>SQL Server Express との互換性を保持する必要が Visual Studio でデータベースを使用するには  
  
-   Visual Studio では、アップグレードしなくても、プロジェクトを開きます。  
  
    -   実行するには、プロジェクトを選択、 **f5 キーを押して**キー。  
  
    -   データベースを編集するに .mdf ファイルを開きます**ソリューション エクスプ ローラー**でノードを展開および**サーバー エクスプ ローラー**データベースを使用します。  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>既定のデータベース エンジンを SQL Server Express を作成するには  
  
1.  メニュー バーで、次のように選択します。**ツール**、**オプション**です。  
  
2.  **オプション** ダイアログ ボックスで、展開、**データベース ツール**オプション、および選択**データ接続**です。  
  
3.  **SQL Server インスタンス名**テキスト ボックスで、SQL Server Express またはを使用する LocalDB のインスタンスの名前を指定します。 指定する場合は、インスタンスがという名前が、`.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`です。  
  
4.  **[OK]** ボタンを選択します。  
  
    SQL Server Express をアプリケーションの既定のデータベース エンジンとなります。

## <a name="see-also"></a>関連項目

[Visual Studio でのデータへのアクセス](accessing-data-in-visual-studio.md)
