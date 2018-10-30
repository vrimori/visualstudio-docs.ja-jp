---
title: SQL Server サンプル データベースのインストール |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6cd9260f29d8e46f66e54fec8cb24ae6857eb05
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217864"
---
# <a name="install-sql-server-sample-databases"></a>SQL Server サンプル データベースをインストールします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
サンプル データベースは、SQL および LINQ クエリ、データ バインド、Entity Framework のモデル化して試してみる場合に便利です。  各データベース製品には、独自のサンプル データベースがあります。 Northwind と AdventureWorks は、人気のある 2 つの SQL Server サンプル データベースです。  
  
 **AdventureWorks**は現在のサンプル データベースを SQL Server の製品に対して提供します。 .Mdf ファイルとしてダウンロードすることができます、 [codeplex の AdventureWorks ページ](http://msftdbprodsamples.codeplex.com/)します。 バージョンがある定期的かつ軽量な (LT)、データベースの使用可能なここです。 ほとんどのシナリオでは、LT バージョンではあまり複雑ではお勧めします。  
  
 **Northwind**は長年にわたって使用されている比較的単純な SQL Server データベースです。 .Bak ファイルとしてダウンロードすることができます、 [CodePlex で Northwind データベース ページ](https://northwinddatabase.codeplex.com/)します。 アクセス許可の問題を回避するには、ユーザー フォルダーの下ではない新しいフォルダーにファイルを解凍します。  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Visual Studio の .bak ファイルからデータベースを復元するには  
  
1.  Microsoft SQL Server データベースをバックアップする場合、.bak ファイルになります。 データベース ファイルとして再使用可能なをファイル .bak にする必要があります*復元*します。 メイン メニューで、次のように選択します。**ビュー** > **SQL Server オブジェクト エクスプ ローラー**します。 表示されない場合は、インストールする必要があります。 移動して**コントロール パネル** > **プログラムと機能**Microsoft Visual Studio 2015 を検索し、クリックして、**変更**ボタンをクリックします。 インストールされているコンポーネントの一覧は、インストーラー ウィンドウが表示されたら、選択、 **SQL Server オブジェクト エクスプ ローラー**チェック ボックスをオンし、インストールを続行します。  
  
2.  SQL Server オブジェクト エクスプ ローラーで、SQL Server データベース エンジン (たとえば、localdb) を右クリックして**新しいクエリ**します。  
  
     ![SQL Server オブジェクト エクスプ ローラーの新しいクエリ](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server オブジェクト エクスプ ローラーの新しいクエリ")  
  
3.  最初に、.bak ファイル内のデータベースとログ ファイルの論理名が必要です。 これを取得する SQL クエリ エディターにこのクエリを入力し、緑色を選択**実行**ウィンドウの上部にあるボタンをクリックします。 .Bak ファイルを指すために必要な場合は、ファイルのパスを変更します。  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     [結果] ウィンドウに表示される論理名を書き留めます。  Northwind データベースでは、2 つの論理名に Northwind と Northwind_log を使用します。  
  
4.  データベースを作成するには、このクエリを実行するようになりました。 独自のソースと変換先のパス、論理データベース名、および Northwind 用の物理ファイル名を適切なに置き換えてください。 .Mdf と .ldf ファイルの拡張機能を保持します。  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5.  SQL Server オブジェクト エクスプ ローラーを右クリックし、**データベース**ノード、およびするが、Northwind データベースのノードに表示されます。 ない場合は、データベースを選択します右クリックし、**新しいデータベースの追加**します。 名前と作成した .mdf ファイルの場所を入力します。  
  
6.  データベースは、Visual Studio でのデータ ソースとして使用する準備ができました。  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>SQL Server Management Studio の .bak ファイルからデータベースを復元するには  
  
1.  SQL Server Management Studio のダウンロード サイトからダウンロードします。  
  
2.  SSMS で**オブジェクト エクスプ ローラー**ウィンドウを右クリックし、**データベース**ノードを選択**データベースの復元**、し .bak ファイルの場所を指定します。  
  
     ![SSMS の データベースの復元](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS の データベースの復元")

