---
title: '方法: TableAdapter クエリの作成 |Microsoft Docs'
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
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f7d4bd84d5cd4538d06048fd6953fa95fc344da0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539495"
---
# <a name="how-to-create-tableadapter-queries"></a>方法 : TableAdapter クエリを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter クエリは、SQL ステートメントまたはストアド プロシージャをアプリケーションがデータベースに対して実行できます。  
  
 アプリケーションで必要な数だけ TableAdapter にクエリを追加します。 TableAdapter クエリは、TableAdapter のメソッドとして表示されます。 というクエリを作成するときに`FillByCity`city の値を表すパラメーターを受け取る、クエリは、TableAdapter に追加されます。 適切な種類のパラメーターを引数として使用する型指定されたメソッドとして追加されます: この場合は、city の値を表す文字列。 任意のオブジェクトには、任意のメソッドと同様、TableAdapter クエリを呼び出します。 たとえば、次のコードの実行、`FillByCity`クエリと塗り、`Customers`テーブルの city の値を持つすべての顧客と`Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 TableAdapter クエリは、データ テーブルを設定できます (`Fill`と`FillBy`クエリ)、クエリによって返されるデータが格納されて、新しいデータ テーブルを返すか (`GetData`と`GetDataBy`クエリ)。  
  
 既存の Tableadapter にクエリを追加するにを実行して、 [TableAdapters の編集](../data-tools/editing-tableadapters.md)します。 (任意の TableAdapter を右クリックし、**クエリの追加**)。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>データセット デザイナーでクエリを作成します。  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>データセット デザイナーで TableAdapter にクエリを追加するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  目的の TableAdapter を右クリックして**クエリの追加**します。  
  
     - または -  
  
3.  ドラッグ、**クエリ**から、**データセット**のタブ、**ツールボックス**をデザイナーでのテーブルにします。  
  
     **TableAdapter クエリ構成ウィザード**が開きます。  
  
4.  ウィザードを完了します。クエリは、TableAdapter に追加されます。  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Windows アプリケーションでのフォーム上に直接クエリを作成します。  
 使用してクエリを追加するには、フォーム上に、TableAdapter のインスタンスがある場合、[検索条件ビルダー ダイアログ ボックス](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)、追加、<xref:System.Windows.Forms.ToolStrip>を任意の入力、クエリに必要なパラメーターを受け入れるフォームにコントロールと同様に、クエリを実行するボタンをクリックします。  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>検索条件 ダイアログ ボックスを使用して TableAdapter にクエリを追加するには  
  
1.  コンポーネント トレイに TableAdapter を選択します。  
  
2.  TableAdapter のスマート タグをクリックし、選択**クエリの追加**します。  
  
3.  ダイアログ ボックスを完了し、TableAdapter にクエリを追加します。 詳細については、次を参照してください。[検索条件ビルダー ダイアログ ボックス](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)します。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法: TableAdapter クエリの編集](../data-tools/how-to-edit-tableadapter-queries.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [方法: Windows フォームの BindingNavigator コントロールを使用してデータを移動します。](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [チュートリアル : 複数のクエリによる TableAdapter の作成](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)