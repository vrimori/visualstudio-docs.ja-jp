---
title: '方法: Northwind データベースへの接続 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3f64fa378029546f7a3126b324c282f6a91d7231
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897635"
---
# <a name="how-to-connect-to-the-northwind-database"></a>方法: Northwind データベースへの接続
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio を使ったデータベース アプリケーションの作成を学習するには、Northwind データベースに接続して、製品のドキュメントに含まれている多くの例を実行します。 実行する例に応じて、SQL Server のデータベース、または Microsoft Access や SQL Server などのデータベース ファイルに接続します。  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Northwind データベースへのデータ接続の作成  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>Northwind データベース (SQL Server) へのデータ接続を作成するには  
  
1. **ビュー** ] メニューの [選択**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
2. **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、ショートカット メニューを開き**データ接続**選択**接続の追加**.  
  
    選択した後**接続の追加**、いずれか、**データ ソースの選択** ダイアログ ボックスまたは**接続の追加** ダイアログ ボックスが表示されます。  
  
3. 場合、**データ ソースの選択**選択 ダイアログ ボックスが表示されたら、 **Microsoft SQL Server**、選び、 **OK**します。  
  
    場合、**接続の追加** ダイアログ ボックスが表示されます、**データ ソース**ない**Microsoft SQL Server (SqlClient)**、選択、**変更**ボタンをクリックする、**データ ソースの変更**ダイアログ ボックスで、 **Microsoft SQL Server**、選択し、 **OK**ボタン。  
  
4. **サーバー名**一覧で、Northwind データベースが配置されているサーバーの名前を指定します。  
  
5. 選択するか、SQL Server および Northwind データベースのバージョンの要件に応じて**Windows 認証を使用**選択または**SQL Server 認証を使用**ユーザー名を入力し、SQL Server を実行しているコンピューターにログオンするパスワード。  
  
6. Northwind データベースを選択して、**を選択するか、データベース名を入力**一覧。  
  
7. 選択**Test-connection**を Northwind データベースへの接続を確認します。  
  
8. **[OK]** をクリックします。  
  
    Northwind データベースへのデータ接続の追加を**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
   SQL Server データベースのリモート インスタンスに接続できるだけでなく、データベースを含む実際のファイルに直接接続することもできます。 これにより、アプリケーションの一部として配置可能なプロジェクトに、データベース ファイルを直接追加できるようになります。 次のローカル データベース ファイルは現在サポートされています: SQL Server Compact データベース ファイル (.sdf) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] SQL Server Express データベース ファイル (.mdf)、および Microsoft Access データベース ファイル (.mdb または .accdb)。  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>Northwind データベース (SQL Server データベース ファイル (.mdf)) へのデータ接続を作成するには  
  
1.  **ビュー** ] メニューの [選択**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
2.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、ショートカット メニューを開き**データ接続**選択**接続の追加**.  
  
     選択した後**接続の追加**、いずれか、**接続の追加** ダイアログ ボックスまたは**データ ソースの選択** ダイアログ ボックスが表示されます。  
  
3.  場合、**データ ソースの選択**選択 ダイアログ ボックスが表示されたら、 **Microsoft SQL Server データベース ファイル**、選択し、 **OK**します。  
  
4.  場合、**接続の追加**ことを確認します ダイアログ ボックスが表示されたら、**データソース**に設定されている**Microsoft SQL Server データベース ファイル (SqlClient)** します。 設定されていない場合**Microsoft SQL Server データベース ファイル (SqlClient)**、選択**変更**を開く、**データ ソースの変更** ダイアログ ボックスで、選択 **』Server データベース ファイル**、選択し、 **OK**ボタンをクリックします。  
  
5.  選択**参照**Northwind データベースを含む .mdf ファイルを検索します。  
  
6.  選択するか、Northwind データベースのバージョンの要件に応じて**Windows 認証を使用**選択または**SQL Server 認証**ユーザー名とパスワードへのログオンを入力し、SQL Server を実行しているコンピューター。  
  
7.  **[OK]** を選択します。  
  
     Northwind データベースへのデータ接続の追加を**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] には、Northwind データベース ファイル (.mdf) に適用される変更があります。 詳しくは、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>Northwind データベース (Access データベース ファイル (.mdb または .accdb)) へのデータ接続を作成するには  
  
1.  **ビュー** ] メニューの [選択**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
2.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、ショートカット メニューを開き**データ接続**選択**接続の追加**.  
  
     選択した後**接続の追加**、いずれか、**接続の追加** ダイアログ ボックスまたは**データ ソースの選択** ダイアログ ボックスが表示されます。  
  
3.  場合、**データ ソースの選択**選択 ダイアログ ボックスが表示されたら、 **Microsoft Access データベース ファイル**、選び、 **OK**します。  
  
4.  場合、**接続の追加**ことを確認します ダイアログ ボックスが表示されたら、**データソース**に設定されている**Microsoft Access データベース ファイル**します。 設定されていない場合**Microsoft Access データベース ファイル**、選択**変更**を開く、**データ ソースの変更** ダイアログ ボックスで、選択**Microsoft Access データベースファイル**、選択し、 **OK**ボタンをクリックします。  
  
5.  選択**参照**Northwind データベースを含む .mdb または .accdb ファイルを検索します。  
  
6.  使用しているバージョンによっては Northwind データベースでユーザー名とパスワードが必要になるため、状況に応じてこれらを入力します。  
  
7.  **[OK]** をクリックします。  
  
     Northwind データベースへのデータ接続の追加を**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
## <a name="see-also"></a>関連項目  
 [方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)   
 [Microsoft Access 2010 を使用したデータ プログラミング](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)