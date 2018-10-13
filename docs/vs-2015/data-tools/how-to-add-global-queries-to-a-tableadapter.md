---
title: '方法: TableAdapter にグローバル クエリの追加 |Microsoft Docs'
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd185c9a6803a5e66b1fdaac0f040815328ddb82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193896"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>方法: TableAdapter にグローバル クエリの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*グローバル クエリ*は 1 つの (スカラー) 値または値を返す SQL クエリ。 通常、グローバル関数は、挿入、更新、削除、およびテーブル、または特定の順序ですべての項目の合計料金で顧客の数を返すなどの情報の集計などのデータベース操作を実行します。  
  
 グローバル クエリを実行して追加する、 **TableAdapter クエリ構成ウィザード**内から、**データセット デザイナー**します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>グローバル クエリ データセットを追加するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  ドラッグ、**クエリ**から、**データセット**のタブ、**ツールボックス**の空の領域に、**データセット デザイナー**します。  
  
     [TableAdapters の編集](../data-tools/editing-tableadapters.md)が開きます。  
  
3.  使用するクエリの接続を選択します。 一覧からいずれかを選択するか、新しい接続を作成します。 新しい接続を作成する場合、アプリケーション構成ファイルに保存するオプション必要があります。 詳細については、次を参照してください。[方法: 接続文字列の編集の保存および](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)します。  
  
4.  SQL ステートメントまたはストアド プロシージャを使用するかどうかを選択します。  
  
5.  使用するストアド プロシージャを選択するか、または、**クエリの種類を選択**ページ、ウィザードの選択 をクリックしてクエリの種類**次**。  
  
6.  たとえば、目的のタスクを実行するクエリの指定`SELECT COUNT(*) AS CustomerCount FROM Customers`します。  
  
    > [!NOTE]
    >  直接クエリをドラッグする、**データセット デザイナー**はスカラー (単一) 値だけを返すメソッドを作成します。 クエリまたはストアド プロシージャを選択する複数の単一の値を返す可能性があります、中に、ウィザードによって作成されたメソッドは、単一の値を返すのみ。 たとえば、クエリは、返されるデータの最初の行の最初の列を返す可能性があります。  
  
7.  ウィザードを完了します。クエリに追加、**データセット デザイナー**します。 クエリを実行する方法の詳細については、次を参照してください。[方法: TableAdapter クエリの実行](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593)します。  
  
## <a name="see-also"></a>関連項目  
 [作成し、Tableadapter を構成します。](../data-tools/create-and-configure-tableadapters.md)   
 [方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [方法: Windows フォームの BindingNavigator コントロールを使用してデータを移動します。](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)