---
title: Access データベース (Windows フォーム) のデータに接続します。
ms.date: 09/15/2017
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f1d0b5d2d0391d401394929e16d5bfc97aa6d555
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282640"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Access データベース (Windows フォーム) のデータに接続します。
Access データベースに接続することができます (いずれか、 *.mdf*ファイルまたは *.accdb*ファイル) Visual Studio を使用します。 接続を定義した後に、データが、**データソース**ウィンドウ。 ここから、テーブルまたはビューをフォームにドラッグできます。

## <a name="prerequisites"></a>前提条件
 これらの手順を使用するには、Windows フォーム アプリケーション プロジェクトと Access データベースが必要です (*.accdb*ファイル) または Access 2000-2003 データベース (*.mdb*ファイル)。 ファイルの種類に対応する手順に従ってください。

## <a name="creating-the-dataset-for-an-accdb-file"></a>.Accdb ファイルのデータセットの作成
 次の手順を使用して、Access 2013、Office 365、Access 2010、または Access 2007 によって作成されたデータベースに接続することができます。

#### <a name="to-create-the-dataset"></a>データセットを作成するには

1.  データに接続する Windows フォーム アプリケーションを開きます。

2.  **ビュー**メニューの **その他の Windows** > **データソース**します。

     ![[表示]、[その他のウィンドウ]、[データ ソース]](../data-tools/media/viewdatasources.png)

3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

     **データ ソース構成ウィザード**が開きます。

4.  選択**データベース**上、**データ ソースの種類を選択**ページ、し、 **次へ**。

5.  選択**データセット**上、**データベース モデルの選択**ページ、し、 **次へ**。

6.  **データ接続の選択**] ページで、[**新しい接続**新しいデータ接続を構成します。

     **接続の追加** ダイアログ ボックスが表示されます。

7.  選択、**変更**横に、**データソース**テキスト ボックス。

     **データ ソースの変更** ダイアログ ボックスが表示されます。

8.  データ ソースの一覧で選択**\<他\>** します。 **データ プロバイダー**ドロップダウンを選択します **.NET Framework Data Provider for OLE DB**を選択し、 **OK**します。

9. 戻り、**接続の追加**ダイアログ ボックスで、 **Microsoft Office 12.0 Access Database Engine OLE DB Provider**から、 **OLE DB Provider**ドロップダウンします。

     ![OLE DB プロバイダーの Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png)

     > [!NOTE]
     >  表示されない場合**Microsoft Office 12.0 Access Database Engine OLE DB Provider**ドロップダウン OLE DB プロバイダーをインストールする必要があります、 [2007 Office system ドライバー: データ接続コンポーネント](https://www.microsoft.com/download/confirmation.aspx?id=23734)します。

9. **サーバーまたはファイル名**テキスト ボックスに、パスを指定し、ファイルの名前、 *.accdb*ファイルへの接続を選択する**OK**。 (データベース ファイルにユーザー名とパスワードがある場合を指定して選択する前に**OK**)。

10. 選択**次**で、**データ接続の選択**ページ。

     データ ファイルは、現在のプロジェクトにないことを示すダイアログ ボックスが表示されます。 **[はい]** または **[いいえ]** をクリックします。

11. 選択**次**で、**接続文字列をアプリケーション構成ファイルに保存**ページ。

12. 展開、**テーブル**上のノード、**データベース オブジェクトの選択**ページ。

13. 任意のテーブルまたはビュー、データセット内に指定し、選択**完了**します。

     データセットが、プロジェクトに追加され、テーブルとビューに表示されます、**データソース**ウィンドウ。

## <a name="create-the-dataset-for-an-mdb-file"></a>.Mdb ファイルのデータセットを作成します。
 実行して、データセットを作成して、**データ ソース構成ウィザード**します。

#### <a name="to-create-the-dataset"></a>データセットを作成するには

1.  データに接続する Windows フォーム アプリケーションを開きます。

2.  **ビュー**メニューの **その他の Windows** > **データソース**します。

     ![[表示]、[その他のウィンドウ]、[データ ソース]](../data-tools/media/viewdatasources.png)

3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

     **データ ソース構成ウィザード**が開きます。

4.  選択**データベース**上、**データ ソースの種類を選択**ページ、し、 **次へ**。

5.  選択**データセット**上、**データベース モデルの選択**ページ、し、 **次へ**。

6.  **データ接続の選択**] ページで、[**新しい接続**新しいデータ接続を構成します。

7.  データ ソースがない場合**Microsoft Access データベース ファイル (OLE DB)**、**変更**を開く、**データ ソースの変更**] ダイアログ ボックスを選択します**Microsoftデータベース ファイルにアクセス**、し、[ **OK**します。

8.  **データベース ファイル名**の名前とパスを指定、 *.mdb*ファイルへの接続を選択する**OK**します。

     ![Access データベース ファイルへの接続を追加](../data-tools/media/dataaddconnectionaccessmdb.png)

9. 選択**次**で、**データ接続の選択**ページ。

10. 選択**次**で、**接続文字列をアプリケーション構成ファイルに保存**ページ。

11. 展開、**テーブル**上のノード、**データベース オブジェクトの選択**ページ。

12. 任意のテーブルまたはビュー、データセット内に指定し、選択**完了**します。

     データセットが、プロジェクトに追加され、テーブルとビューに表示されます、**データソース**ウィンドウ。

## <a name="security"></a>セキュリティ
 機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、次を参照してください。[接続情報の保護](/dotnet/framework/data/adonet/protecting-connection-information)します。

## <a name="next-steps"></a>次の手順
 先ほど作成したデータセットで提供されて、**データソース**ウィンドウ。 これで、次のタスクのいずれかを実行できます。

-   内の項目を選択して、**データ ソース**ウィンドウ、フォームにドラッグし、(を参照してください[Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md))。

-   データ ソースを開き、**データセット デザイナー**データセットを構成するオブジェクトを追加または編集します。

-   検証ロジックを追加、<xref:System.Data.DataTable.ColumnChanging>または<xref:System.Data.DataTable.RowChanging>データセット内のデータ テーブルのイベント (を参照してください[データセットのデータの検証](../data-tools/validate-data-in-datasets.md))。

## <a name="see-also"></a>関連項目

- [接続を追加する](../data-tools/add-new-connections.md)