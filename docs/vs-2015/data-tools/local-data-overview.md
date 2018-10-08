---
title: ローカル データの概要 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b2bd594ba017a07ad3886a9aeb4b59d6f479a708
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537014"
---
# <a name="local-data-overview"></a>ローカル データの概要
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データ アプリケーションを開発する場合、通常はお勧め、データベースのローカル コピーを使用する運用データにエラーが発生しないようにします。 2 人の開発者は、検出が難しい方法で対話できるエラーを引き起こす場合は、潜在的な問題を作成も他の開発者とテスト データベースを共有します。 ローカル コンピューターで、独自のテスト データを使用して、これらすべての落とし穴を回避できます。 ほとんどの場合、すべてのデータベース システムでは、ローカル データ ファイルを作成できます。 .NET プロジェクトの場合は、Visual Studio は、ローカルの SQL Server データベース ファイル (.mdf) および Microsoft Access データベース ファイル (.mdb) 用に特別なサポートを提供します。  
  
 Visual Studio には、これらのシナリオがサポートされています。  
  
1.  
  
2.  
  
-  
  
-  
  
-   ソリューション エクスプ ローラーでソリューション ノードをクリックしを選択する SQL Server データベース プロジェクトを作成**追加&#124;新しいプロジェクト**します。  左側のウィンドウで次のように選択します。 **SQL Server&#124;データベース**プロジェクトと、[ok] をクリックします。 ソリューション エクスプ ローラーで、ローカル データベース ファイルをインポートするデータベース プロジェクト ノードを右クリックし、プロジェクトによって生成されたデータベースに接続するアプリケーションを開発します。 開発し、アプリケーションを開発するいると同時に、データベース スキーマを変更する場合に適しています。  
  
     ![データベースをデータベース プロジェクトにインポート](../data-tools/media/raddata-import-database-into-database-project.png "raddata インポート データベースにデータベース プロジェクト")  
  
-   新しいデータベースを作成する場合は、まず追加、**サービス ベースのデータベース ファイル**をプロジェクトに (**プロジェクト&#124;新しい項目の追加)** します。 (Localdb) \MSSQLocalDB は、既定では、ローカル コンピューターの既定の SQL Server インスタンスに接続されている新しい .mdf ファイルが作成されます。 データベースは、サーバー エクスプ ローラーに表示されます。 ノードを展開し、テーブル、ビュー、関数などの新しいデータベース オブジェクトを追加するノードを右クリックします。  
  
 SQL Server Express LocalDB の詳細については、次を参照してください。 [Introducing LocalDB,、改善 SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375)と[LocalDB: My Database があるでしょうか。](http://go.microsoft.com/fwlink/?LinkId=234376) 、Microsoft web サイト。  
  
 次の表に、アプリケーションをローカル データに接続する方法を説明するトピックへのリンクを示します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[デザイナーを使用して SQL データベースを作成する](../data-tools/create-a-sql-database-by-using-a-designer.md)|データ機能のテストとアプリケーションのビルドを行うために使用できるローカル データベース ファイルを作成するための手順を示します。|  
|[チュートリアル: ローカル データベース ファイル内のデータへの接続 (Windows フォーム)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|簡単な Windows アプリケーションを作成する際に SQL Server Express の LocalDB データベースに接続するための手順を示します。|  
|[Access データベース内のデータへの接続 (Windows フォーム)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Microsoft Access データベースへの接続の詳細な手順を提供します。|  
|[方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、SQL Server Compact、SQL Server Express、および Access の Northwind サンプル データベースに接続する方法の詳細について説明します。|  
  
## <a name="use-the-connection-string"></a>接続文字列を使用します。  
 これが最も簡単な方法と、サード パーティ製データベースを使用して、アプリケーションは、データベースからのみ読み取るときをお勧めします。 データベース ファイルは、ローカル コンピューターをアプリケーションにアクセスするためのアクセス許可を持つと、データベース システムをサポートするには、どこにでも配置できます。  
  
1.  (省略可能)新しい接続を作成する」の説明に従って[新しい接続を追加](../data-tools/add-new-connections.md)します。 サード パーティ製データベースと .mdf ファイルを既に接続文字列を認識し、データ バインドを行うまたはされません Entity Framework のクラスやデータセットなどのデータ ソースを使用して、この手順は必要はありません。 だけ、接続文字列を使用して、ローカル ファイルへの接続します。 .Mdf ファイルを参照してください。 [.mdf ファイルをアップグレードする](../data-tools/upgrade-dot-mdf-files.md)と[接続を確立する](https://msdn.microsoft.com/en-us/library/ms254507.aspx)します。  
  
2.  (省略可能)Entity Framework や LINQ to SQL でのデータセットを使用している場合は、データ ソース構成ウィザードを使用して、データ ソースを作成します。 詳細については、「[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)」を参照してください。  
  
## <a name="add-an-existing-mdf-to-your-project"></a>既存の .mdf ファイルをプロジェクトに追加します。  
 挿入、削除またはデータを更新するは、アプリケーション使用可能な元のファイルのコピーを保持する場合は、ファイルをプロジェクトに追加し、検討してください。 項目のプロパティを設定するにはそうと**出力ディレクトリにコピー**に**常にコピー**または**新しい場合はコピー**、およびアプリケーションを開発します。 アプリケーションをビルドするたびにでは、出力フォルダーに、元のデータベースがコピーされ、アプリケーションの変更は、コピーで実行されます。 この方法で、元のデータのクリーンなコピーを常に、します。  
  
1.  使用**Windows エクスプ ローラー**にドラッグ アンドに Visual Studio でソリューション エクスプ ローラーでプロジェクト ノードの現在の場所から .mdf ファイルをドロップします。  場合は、ファイルは localDB インスタンスに既に結び付けられている、最初にデタッチする必要があります。 プロジェクトにドロップすると、Visual Studio は自動的に再接続し、既定の localDB インスタンスに。  
  
2.  新しいデータベース ノードを右クリックし、プロパティを選択します。 コピーの動作を選択しますか**常にコピー**または**新しい場合はコピー**します。  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>SQL Server データベース プロジェクトを作成し、データベースのインポート  
 これは、する開発を行うことはデータベース自体、おそらく列またはテーブルを追加またはデータ型を変更するときに、適切なオプションです。  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>各プロジェクトはデータベースの 2 つのコピーを含む  
 出力にルート プロジェクト フォルダーからデータベース ファイルがコピーされる可能性がありますプロジェクトをビルドするときに**bin**フォルダー。 この動作によって異なります、**出力ディレクトリにコピー**ファイルのプロパティとそのプロパティの既定値は、使用しているデータベース ファイルの種類によって異なります。  
  
 表示する、 **bin**フォルダー**ソリューション エクスプ ローラー**、選択、 **すべてのファイル**ツールバーのボタン。  
  
> [!NOTE]
>  **出力ディレクトリにコピー**に web プロジェクトまたは C++ プロジェクト プロパティは適用されません。  
  
 使用して、データベース スキーマまたはデータを編集する場合にのみ、ルート プロジェクト フォルダー内のデータベース ファイルが変更された**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**またはその他の[Visualデータベース ツール](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)します。  
  
 データベースを変更するアプリケーション開発時にデータを変更すると、 **bin**フォルダー。 たとえば、F5 キーを押してアプリケーションをデバッグすると、そのフォルダー内のデータベースに接続されます。  
  
|値**出力ディレクトリにコピー**プロパティ|動作|  
|----------------------------------------------------|--------------|  
|**新しい場合はコピー** (既定値の .sdf ファイル)|データベース ファイルがプロジェクト ディレクトリからコピーされた、 **bin**ディレクトリ、プロジェクトをビルドする最初の時間。 **日時**ファイルのプロパティは、プロジェクトをもう一度ビルドするたびと比較されます。 プロジェクト フォルダー内のファイルが新しい場合、そのファイルにコピーされて、 **bin**フォルダーを前のファイルを置き換えます。 それ以外の場合には、ファイルはコピーされません。 **注意:** .mdb ファイルまたは .mdf ファイルのこの値はお勧めしません。 データベース ファイルはデータが変更されていない場合でも変更される場合があります。 ファイルは、単に接続を開く場合に新しいマークできます (たとえば、展開、**テーブル**ノード**サーバー エクスプ ローラー**)。|  
|**常にコピー** (既定値の .mdf ファイルおよび .mdb ファイル)|データベース ファイルがプロジェクト ディレクトリからコピーされた、 **bin**ディレクトリ、アプリケーションをビルドするたびにします。 出力フォルダー内のデータ ファイルに行った変更は、次にアプリケーションを実行したときに上書きされます。|  
|**コピーしません。**|システム内のファイルが上書きされたり、 **bin**ディレクトリ。 アプリケーションは、出力ディレクトリ内のデータベース ファイルを指す接続文字列を動的に作成します。 したがって、出力ディレクトリ内のデータとプロジェクト ディレクトリのデータを一致させるためには、出力ディレクトリに手動でファイルをコピーする必要があります。|  
  
## <a name="common-issues-with-local-data"></a>ローカル データの一般的な問題  
 次の表は、ローカル データ ファイルを使用するときに発生する可能性のある一般的な問題を示しています。  
  
|懸案事項|説明|  
|-----------|-----------------|  
|アプリケーションをテストしてデータを変更し、次回アプリケーションを実行すると必ず変更内容が失われる|値、**出力ディレクトリにコピー**プロパティは**新しい場合はコピー**または**常にコピー**します。 出力フォルダーのデータベース (アプリケーションをテストする際に変更されるデータベース) は、プロジェクトをビルドするたびに上書きされます。 詳細については、次を参照してください。[方法: プロジェクトでのローカル データ ファイルの管理](../data-tools/how-to-manage-local-data-files-in-your-project.md)します。|  
|データ ファイルがロックされているというメッセージが表示される。|Access (.mdb ファイル) : Access などの別のプログラムでファイルが開かれていないことを確認します。<br /><br /> SQL Server Express (.mdf ファイル) : Visual Studio IDE の外部でデータ ファイルをコピー、移動、または名前を変更しようとすると、SQL Express はデータ ファイルをロックします。|  
|複数のユーザーが同じデータベースを同時にアクセスしようとすると、アクセスは拒否されます。|Visual Studio ではの活用*ユーザー インスタンス*、機能の一つの SQL Server Express ユーザーごとに個別の SQL Server インスタンスを作成します。 1 人のユーザーがファイルにアクセスすると、その後にアクセスするユーザーは接続できません。 この問題は、インターネット インフォメーション サービス (IIS) は一般に個別のアカウントで実行されるので、ASP.NET 開発サーバーと IIS で Web アプリケーションを実行しようとする場合などに発生します。|  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ローカル データベース ファイル (Windows フォーム) 内のデータへの接続](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Access データベース内のデータへの接続 (Windows フォーム)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)