---
title: 'チュートリアル: データセット デザイナーでの DataTable の作成 |Microsoft Docs'
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1f0f31528239794b9c7a3b4a4bf98542ed4bbcf2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299963"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>チュートリアル : データセット デザイナーでの DataTable の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルを作成する方法を説明する、 <xref:System.Data.DataTable> (せずに、TableAdapter) を使用して、**データセット デザイナー**。 Tableadapter を含むデータ テーブルを作成する方法の詳細については、次を参照してください。[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい Windows アプリケーション プロジェクトを作成します。  
  
-   アプリケーションに新しいデータセットの追加  
  
-   データセットに新しいデータ テーブルの追加  
  
-   データ テーブルに列を追加  
  
-   テーブルの主キーの設定  
  
## <a name="creating-a-new-windows-application"></a>新しい Windows アプリケーションの作成  
  
#### <a name="to-create-a-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プログラミング言語を選択して、**プロジェクトの種類**ウィンドウ。  
  
3.  クリックして**Windows アプリケーション**で、**テンプレート**ウィンドウ。  
  
4.  プロジェクトの名前`DataTableWalkthrough`、 をクリックし、 **OK**します。  
  
     Visual Studio にプロジェクトが追加**ソリューション エクスプ ローラー**を表示および**Form1**デザイナー。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>アプリケーションへの新しいデータセットの追加  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>プロジェクトに新しいデータセット項目を追加するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
     新しい項目の追加 ダイアログ ボックスが表示されます。  
  
2.  **テンプレート**ボックスで、**データセット**します。  
  
3.  **[追加]** をクリックします。  
  
     という名前のファイルを追加する visual Studio **DataSet1.xsd**プロジェクトで開くと、**データセット デザイナー**します。  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>データセットに新しい DataTable の追加  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>データセットに新しいデータ テーブルを追加するには  
  
1.  ドラッグ、 **DataTable**から、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**します。  
  
     という名前のテーブル**DataTable1**データセットに追加されます。  
  
    > [!NOTE]
    >  TableAdapter を含むデータ テーブルを作成するを参照してください。[チュートリアル: 複数のクエリによる TableAdapter の作成](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)です。  
  
2.  タイトル バーをクリックします。 **DataTable1**名前を変更および`Music`します。  
  
## <a name="adding-columns-to-the-data-table"></a>データ テーブルに列を追加  
  
#### <a name="to-add-columns-to-the-data-table"></a>データ テーブルに列を追加するには  
  
1.  右クリックし、**音楽**テーブル。 をポイント**追加**、 をクリックし、**列**します。  
  
2.  列の名前を付けます`SongID`します。  
  
3.  **[プロパティ]** ウィンドウで、 <xref:System.Data.DataColumn.DataType%2A> プロパティを <xref:System.Int16?displayProperty=fullName>に設定します。  
  
4.  このプロセスを繰り返して、次の列を追加します。  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>テーブルの主キーの設定  
 すべてのデータ テーブルには、主キーを持つ必要があります。 主キーは、データ テーブル内の特定のレコードを一意に識別します。  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>データ テーブルの主キーを設定するには  
  
-   右クリックし、 **SongID**列、およびクリック**主キーの設定**します。  
  
     鍵のアイコンが横に表示されます、 **SongID**列。  
  
## <a name="saving-your-project"></a>プロジェクトの保存  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>DataTableWalkthrough プロジェクトを保存するには  
  
-   **ファイル** メニューのをクリックして**すべて保存**します。  
  
## <a name="next-steps"></a>次の手順  
 これで、テーブルを作成するアクションを次のいずれかを実行する可能性があります。  
  
|終了|解決方法については、|  
|--------|---------|  
|データを入力するフォームを作成します。|[チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)します。|  
|テーブルにデータを追加します。|[データを DataTable に追加する](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b)します。|  
|テーブルのデータの表示|[DataTable にデータを表示する](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc)します。|  
|データを編集します。|[DataTable の編集](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|テーブルから行を削除します。|[DataRow の削除](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)