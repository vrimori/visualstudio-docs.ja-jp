---
title: .mdf ファイルのアップグレード
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 875208d068c791c0238c110ea0e83b04e18348fc
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117941"
---
# <a name="upgrade-mdf-files"></a>.mdf ファイルのアップグレード

このトピックでは、データベース ファイルをアップグレードするためのオプションを説明します (*.mdf*)、新しいバージョンの Visual Studio をインストールした後。 手順についてには、次のタスクが含まれています。

- 新しいバージョンの SQL Server Express LocalDB を使用するデータベース ファイルをアップグレードします。

- SQL Server Express の新しいバージョンを使用するデータベース ファイルをアップグレードします。

- Visual Studio でのデータベース ファイルを使用して機能しますが、古いバージョンの SQL Server Express または LocalDB との互換性を保持

- 既定のデータベース エンジンを SQL Server Express を行う

Visual Studio を使用してデータベース ファイルを含むプロジェクトを開くことができます (*.mdf*) 以前のバージョンの SQL Server Express または LocalDB を使用して作成されました。 ただしを Visual Studio でプロジェクトの開発を続行するには、そのバージョンの SQL Server Express または Visual Studio と同じコンピューターにインストールされている LocalDB であるか、データベース ファイルをアップグレードする必要があります。 データベース ファイルをアップグレードする場合は、以前のバージョンの SQL Server Express または LocalDB を使用してアクセスできません。

また、ファイルのバージョンが SQL Server Express または現在インストールされている LocalDB のインスタンスとの互換性がない場合、以前のバージョンの SQL Server Express または LocalDB を通じて作成されたデータベース ファイルをアップグレードするように求め可能性があります。 この問題を解決するには、Visual Studio は、ファイルをアップグレードすることを求められます。

> [!IMPORTANT]
> アップグレードする前に、データベース ファイルをバックアップすることをお勧めします。

> [!WARNING]
> アップグレードする場合、 *.mdf* LocalDB 2016 (V13) またはそれ以降の 32 ビットである LocalDB 2014 (V12) で作成されたファイルはできません、32 ビット バージョンの LocalDB でもう一度ファイルを開くことができません。

データベースをアップグレードする前に、次の条件を考慮してください。

-   以前のバージョンと新しいバージョンの Visual Studio の両方で、プロジェクトで作業する場合、アップグレードしないでください。

-   SQL Server Express LocalDB はなくを使用する環境でアプリケーションを使用する場合、アップグレードしないでください。

-   LocalDB から受け入れないために、アプリケーションは、リモート接続を使用する場合にアップグレードしないでください。

-   アプリケーションには、インターネット インフォメーション サービス (IIS) が依存している場合、アップグレードしないでください。

-   サンド ボックス環境でデータベース アプリケーションをテストするデータベースを管理するしたくない場合は、アップグレードを検討します。

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>LocalDB のバージョンを使用するデータベース ファイルをアップグレードするには

1.  **サーバー エクスプ ローラー**を選択、**データベースへの接続**ボタンをクリックします。

2.  **接続の追加** ダイアログ ボックスで、次の情報を指定します。

    -   **データ ソース**: `Microsoft SQL Server (SqlClient)`

    -   **サーバー名**:

        -   既定のバージョンを使用する:`(localdb)\MSSQLLocalDB`します。  これを指定 ProjectV12 または ProjectV13 のいずれかによっては、Visual Studio のバージョンがインストールされているし、最初の LocalDB インスタンスの作成時にします。 **MSSQLLocalDB**ノード**SQL Server オブジェクト エクスプ ローラー**ポイントにバージョンを示しています。

        -   特定のバージョンを使用する:`(localdb)\ProjectsV12`または`(localdb)\ProjectsV13`V12 は LocalDB 2014、V13 は LocalDB 2016。

    -   **データベース ファイルを添付**: プライマリの物理パス *.mdf*ファイル。

    -   **論理名**: ファイルで使用する名前。

3.  **[OK]** ボタンを選択します。

4.  求められたら、選択、**はい**ボタン ファイルをアップグレードします。

    データベースはアップグレードされ、LocalDB データベース エンジンに接続されて、LocalDB の古いバージョンと互換性がありません。

SQL Server Express LocalDB を使用して、接続のショートカット メニューを開き、に接続を変更することもできます。**接続の変更**します。 **接続の変更** ダイアログ ボックスで、サーバー名を変更して`(LocalDB)\MSSQLLocalDB`します。 **プロパティの詳細** ダイアログ ボックスに、必ず**ユーザー インスタンス**に設定されている**False**します。

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>SQL Server Express バージョンを使用するデータベース ファイルをアップグレードするには

1.  データベースへの接続のショートカット メニューを選択**接続の変更**します。

2.  **接続の変更**ダイアログ ボックスで、**詳細**ボタンをクリックします。

3.  **プロパティの詳細**ダイアログ ボックスで、 **OK**サーバー名を変更することがなくボタン。

    SQL Server Express の現在のバージョンと一致するデータベース ファイルはアップグレードされます。

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Visual Studio でデータベースが SQL Server Express との互換性を保持するには

-   Visual Studio では、アップグレードしなくても、プロジェクトを開きます。

    -   プロジェクトを実行するには、選択、 **F5**キー。

    -   データベースを編集するには、開く、 *.mdf*ファイル**ソリューション エクスプ ローラー**でノードを展開および**サーバー エクスプ ローラー**データベースを使用します。

### <a name="to-make-sql-server-express-the-default-database-engine"></a>既定のデータベース エンジンを SQL Server Express を作成するには

1.  メニュー バーで選択**ツール** > **オプション**します。

2.  **オプション** ダイアログ ボックスで、展開、**データベース ツール**オプション、および選択**データ接続**します。

3.  **SQL Server インスタンス名**テキスト ボックスに、SQL Server Express または使用する LocalDB のインスタンスの名前を指定します。 場合は、インスタンスがという名前が指定`.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`します。

4.  **[OK]** ボタンを選択します。

    SQL Server Express をアプリケーションの既定のデータベース エンジンとなります。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](accessing-data-in-visual-studio.md)