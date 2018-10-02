---
title: Access データベース (Windows フォーム) でのデータへの接続 |Microsoft Docs
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
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9ddab545909730a4fe7f94adf59c6cee74c86409
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545517"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Access データベース (Windows フォーム) のデータに接続します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Access データベース (Windows フォーム) でのデータへの接続](https://docs.microsoft.com/visualstudio/data-tools/connect-to-data-in-an-access-database-windows-forms)します。  
  
  
Visual Studio を使用して、Access データベース (.mdf ファイルまたは .accdb ファイル) に接続することができます。 接続を定義した後に、データが、**データソース**ウィンドウ。 ここから、テーブルまたはビューをフォームにドラッグできます。 参照してください、Visual Studio のプロジェクト システムがこれらのローカル データベース ファイルを管理する方法を理解したい場合[方法: プロジェクトでのローカル データ ファイルの管理](../data-tools/how-to-manage-local-data-files-in-your-project.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 これらの手順を使用するには、Windows フォーム アプリケーション プロジェクト、および Access データベース (ファイル.accdb ファイル) または Access 2000-2003 データベース (.mdb ファイル) が必要です。 ファイルの種類に対応する手順に従ってください。  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>.Accdb ファイルのデータセットの作成  
 次の手順を使用して、Access 2013、Office 365、Access 2010、または Access 2007 によって作成されたデータベースに接続することができます。  
  
#### <a name="to-create-the-dataset"></a>データセットを作成するには  
  
1.  データに接続する Windows フォーム アプリケーションを開きます。  
  
2.  **ビュー**メニューの **その他の Windows** > **データソース**します。  
  
     ![その他の Windows のデータ ソースの表示](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。  
  
     ![新しいデータ ソースの追加](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4.  選択**データベース**上、**データ ソースの種類を選択**ページ、し、 **次へ**。  
  
5.  選択**データセット**上、**データベース モデルの選択**ページ、し、 **次へ**。  
  
6.  **データ接続の選択**] ページで、[**新しい接続**新しいデータ接続を構成します。  
  
7.  変更、**データソース**に **.NET Framework Data Provider for OLE DB**します。  
  
     ![OLE DB にデータ プロバイダーを変更](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    >  データ ソースが**Microsoft Access データベース ファイル (OLE DB)** .mdb データベース ファイルにのみそのデータ ソースの種類を使用する最適な選択肢と思えるかもしれません。  
  
8.  **OLE DB Provider**、 **Microsoft Office 12.0 Access Database Engine OLE DB Provider**します。  
  
     ![OLE DB プロバイダーの Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. **サーバーまたはファイル名**、クリックして、接続する .accdb ファイルの名前とパスを指定**OK**します。  
  
    > [!NOTE]
    >  データベース ファイルにユーザー名とパスワードがある場合を指定して選択する前に**OK**します。  
  
10. 選択**次**で、**データ接続の選択**ページ。  
  
11. 選択**次**で、**接続文字列をアプリケーション構成ファイルに保存**ページ。  
  
12. 展開、**テーブル**上のノード、**データベース オブジェクトの選択**ページ。  
  
13. 任意のテーブルまたはビュー、データセット内に指定し、選択**完了**します。  
  
     データセットが、プロジェクトに追加され、テーブルとビューに表示されます、**データソース**ウィンドウ。  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>.Mdb ファイルのデータセットの作成  
 実行して、データセットを作成して、**データ ソース構成ウィザード**します。  
  
#### <a name="to-create-the-dataset"></a>データセットを作成するには  
  
1.  データに接続する Windows フォーム アプリケーションを開きます。  
  
2.  **ビュー**メニューの **その他の Windows** > **データソース**します。  
  
     ![その他の Windows のデータ ソースの表示](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。  
  
4.  選択**データベース**上、**データ ソースの種類を選択**ページ、し、 **次へ**。  
  
5.  選択**データセット**上、**データベース モデルの選択**ページ、し、 **次へ**。  
  
6.  **データ接続の選択**] ページで、[**新しい接続**新しいデータ接続を構成します。  
  
7.  データ ソースがない場合**Microsoft Access データベース ファイル (OLE DB)**、**変更**を開く、**データ ソースの変更**] ダイアログ ボックスを選択します**Microsoftデータベース ファイルにアクセス**、し、[ **OK**します。  
  
8.  **データベース ファイル名**、クリックして、接続する .mdb ファイルの名前とパスを指定**OK**します。  
  
     ![Access データベース ファイルの接続を追加](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. 選択**次**で、**データ接続の選択**ページ。  
  
10. 選択**次**で、**接続文字列をアプリケーション構成ファイルに保存**ページ。  
  
11. 展開、**テーブル**上のノード、**データベース オブジェクトの選択**ページ。  
  
12. 任意のテーブルまたはビュー、データセット内に指定し、選択**完了**します。  
  
     データセットが、プロジェクトに追加され、テーブルとビューに表示されます、**データソース**ウィンドウ。  
  
## <a name="security"></a>セキュリティ  
 機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)」を参照してください。  
  
## <a name="next-steps"></a>次の手順  
 先ほど作成したデータセットで提供されて、**データソース**ウィンドウ。 これで、次のタスクのいずれかを実行できます。  
  
-   内の項目を選択して、**データ ソース**ウィンドウ、フォームにドラッグし、(を参照してください[Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md))。  
  
-   データ ソースを開き、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)データセットを構成するオブジェクトを追加または編集します。  
  
-   検証ロジックを追加、<xref:System.Data.DataTable.ColumnChanging>または<xref:System.Data.DataTable.RowChanging>データセット内のデータ テーブルのイベント (を参照してください[データセットのデータの検証](../data-tools/validate-data-in-datasets.md))。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)

