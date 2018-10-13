---
title: '方法: データ フォーム アプリケーションを Windows に関連する表示 |Microsoft Docs'
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3fd7a29e1de66a5b5fd57dab1adbcf99128001ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215463"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>方法: 関連するデータを Windows フォーム アプリケーションに表示する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

関連データを表示するにはから同じメイン テーブル ノードを共有する項目をドラッグして、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)フォームにします。 たとえば、データ ソースがある場合は、`Customers`テーブルと関連`Orders`テーブルで表示される両方のテーブル (ツリー ビュー) 内の最上位ノードとして、**データソース**ウィンドウ。 [`Customers`] ノードを展開すると列が表示され、一覧の最後の列が、`Orders` テーブルを表す展開可能なノードとして表示されます。 このノードは、顧客に関連する注文を表します。 これは、顧客を選択できるフォームを作成し、その顧客の注文の一覧を表示する場合、表示する各項目をこの 1 つの階層からドラッグできることを意味します。  
  
 ![データ ソース ウィンドウの関係を示す](../data-tools/media/datasources2.gif "DataSources2")  
関連するレコードを表示するデータ バインド コントロールの作成  
  
 ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo")このトピックのビデオ版について、次を参照してください。 [i: Update の関連テーブルの操作方法](http://go.microsoft.com/fwlink/?LinkId=143527)します。  
  
### <a name="to-create-controls-that-display-related-records"></a>関連するレコードを表示するコントロールを作成するには  
  
1.  フォームを開き、 [Windows フォーム デザイナー](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)します。  
  
2.  開く、**データソース**ウィンドウ。 詳細については、次を参照してください。[方法: データ ソース ウィンドウを開く](../data-tools/how-to-open-the-data-sources-window.md)します。  
  
3.  リレーションシップの親テーブルを表すノードを展開します  (親テーブルは、一対多リレーションシップの "一" の側のテーブルです)。  
  
4.  リレーションシップの親テーブルから表示するすべての項目をドラッグして、**データ ソース**ウィンドウから、フォームにします。  
  
5.  親テーブルの列一覧の下部に、関連する子テーブルが展開可能なノードとして表示されます。 表示する項目を、このような関連するノードからフォームにドラッグします。  
  
    > [!NOTE]
    >  個別の関係のないを作成する最上位ノードから項目をドラッグする[BindingSource コンポーネント](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)を促進はしない関連レコード間を移動します。 関連するデータをバインドするには、同じ階層構造ノードにあるテーブルを選択する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [方法: Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)