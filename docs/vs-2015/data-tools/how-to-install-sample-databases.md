---
title: '方法: サンプル データベースのインストール |Microsoft Docs'
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 86dd1914b69dc047c6f8fd9b5d531976141b5ded
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534656"
---
# <a name="how-to-install-sample-databases"></a>方法 : サンプル データベースをインストールする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

多くのデータ例で、サンプル データベース Northwind、Pubs、および AdventureWorks への接続が必要になります。 これらのデータベースには、次の手順に従ってインストールし、接続できます。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>データベースのインストール  
 多くのデータ サンプルでは、Web サイトからダウンロードできるサンプル データベースを使用できることが必要です。 サンプル データベースには、AdventureWorks、Northwind、および Pubs データベースが含まれています。  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>SQL Server 用の Northwind サンプル データベースと Pubs サンプル データベースをインストールするには  
  
1.  移動して、 [Northwind および Pubs サンプル データベース](http://go.microsoft.com/fwlink?linkid=64296)web サイト。  
  
2.  インストーラーをダウンロードして実行します。  
  
     インストーラーは、フォルダーを追加します。 **SQL Server 2000 Sample Databases** 、コンピューター上のルート フォルダーにします。 (例: **C:\SQL Server 2000 Sample Databases**)。  
  
3.  必要なデータベース (Northwind または Pubs) に対応する SQL スクリプトを探します。  
  
    > [!WARNING]
    >  .MDF データベース ファイルは SQL Server の現在のバージョンで使用できる形式に簡単に変換できないため、スクリプトを使用してデータベースを作成することをお勧めします。  
  
4.  **サーバー エクスプ ローラー**データベースをインストールする SQL Server インスタンスへの接続を作成します。 使用する特定の SQL Server が存在しない場合は、Visual Studio と共に自動的にインストールされるデータベースを使用できます。 そのためには次のように指定します。`(localdb)\v11.0`サーバー名として。  
  
     接続を作成するには、次の手順に従います。  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>SQL Server インスタンスへの接続を作成するには  
  
    1.  **サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続**ノード選択**接続の追加**します。  
  
         **接続の追加** ダイアログ ボックスが表示されます。  
  
    2.  Northwind データベースまたは Pubs データベースを作成する SQL Server の名前を指定するか、「(localdb)\v11.0」と入力します。  
  
    3.  **を選択するか、データベース名を入力**、たとえば、tempdb の一覧から任意のデータベースを選択します。  
  
    4.  選択、**接続のテスト**ことすべてが動作していることを確認するボタンをクリックし、選択し、 **OK**ボタン。  
  
         新しい接続ノードに表示されます**サーバー エクスプ ローラー**します。  
  
5.  サーバーの接続ノードのショートカット メニューを選択し、**新しいクエリ**ボタン。  
  
     エディター ウィンドウが開き、空の .sql スクリプト ファイルが表示されます。  
  
6.  instnwnd.sql または instpubs.sql の内容をエディター ウィンドウに貼り付けます。  
  
7.  [クエリの実行] ボタン (クエリ ウィンドウの右上にある、塗りつぶされていない緑色の三角のアイコン) を選択します。  
  
     クエリが成功すると、メッセージ**コマンドが正常に完了した**が表示されます。 これは、Northwind または pubs データベースが作成されたことを意味します。  
  
     次に、サンプル データベースに接続を追加する必要があります。 **サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続**ノード選択**接続の追加**します。  
  
8.  [選択] で、この時間が、前に、選択したサーバーのデータベースまたはデータベース名を入力と同じ選択で、Northwind または pubs データベースを選択し、 **OK**ボタンをクリックします。  
  
     サンプル データベースの [データ接続] の下に、新しいノードが表示されます。  
  
9. エディター ウィンドウを閉じ、クエリ ファイルを保存しないことを確認します。 データベースの作成後は、データベース作成スクリプトを保存する必要はありません。  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>AdventureWorks サンプル データベースをインストールするには  
  
-   AdventureWorks サンプル データベースからのダウンロード、 [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)します。  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>Microsoft Access 用の Northwind サンプル データベースをインストールするには  
  
1.  Microsoft Access 2010 以降では、Northwind のオンライン テンプレートの検索し、選択**デスクトップ Northwind 2007 サンプル データベース**します。  
  
2.  Microsoft Access で、データベース ファイルを Northwind.accdb として保存します。  
  
 Access データベースの新しい拡張子は .accdb です。 参照してください[Microsoft Access 2010 を使用したデータ プログラミング](http://msdn.microsoft.com/library/office/ff965871.aspx)します。 アクセスを使用して、Northwind データベースに接続するを参照してください。[方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 サンプル データベースは例示のみを目的としており、必ずしもセキュリティに関するベスト プラクティスを示しているとは限りません。  
  
## <a name="see-also"></a>関連項目  
 [バージョンとエディションの SQL Server とそのコンポーネントを確認する方法](http://support.microsoft.com/kb/321185)   
 [デザイナーを使用して SQL database を作成します。](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)