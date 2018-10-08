---
title: '方法: データ テーブルの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 596c2760e100bc45eefdde10743b3d9b45490b91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545715"
---
# <a name="how-to-create-data-tables"></a>方法: データ テーブルを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データは、<xref:System.Data.DataTable> オブジェクトのメモリに格納できます  (データセットは <xref:System.Data.DataTable> オブジェクトで構成されます)。通常を使用して Tableadapter を新しいデータ テーブルを作成する、 [TableAdapter 構成ウィザード](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)またはからのデータベース オブジェクトをドラッグして**サーバー エクスプ ローラー**上に、**データセット デザイナー**.  
  
 新しい Tableadapter を作成するときに、データ テーブルが副産物として作成されます、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)もができますも作成する必要がない個別にします。 スタンドアロン データ テーブルをドラッグして作成した、<xref:System.Data.DataTable>オブジェクトから、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**します。  
  
> [!NOTE]
>  プログラムでデータ テーブルを作成するを参照してください。 [DataTable の作成](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414)です。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>TableAdapter を使用するデータ テーブルの作成  
 TableAdapter を使用するデータ テーブルには、テーブルにデータを格納し、変更内容をデータベースに書き戻すメソッドが含まれます。 使用して Tableadapter を作成する、 **TableAdapter 構成ウィザード**またはからのデータベース オブジェクトをドラッグして**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>TableAdapter を使用する新しいデータ テーブルを作成するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳しくは、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  ドラッグ、 **TableAdapter**から、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**します。  
  
     **TableAdapter 構成ウィザード**が開きます。  
  
3.  ウィザードを完了します。 詳細については、次を参照してください[TableAdapter 構成ウィザード。](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>サーバー エクスプローラーで TableAdapter を使用する新しいデータ テーブルを作成するには  
  
1.  データセットを開き、**データ ソース デザイナー**します。  
  
2.  データベース オブジェクト (テーブルなど) からドラッグ**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。  
  
## <a name="creating-a-standalone-datatable"></a>スタンドアロン DataTable の作成  
 スタンドアロン テーブルには、データを格納するために実装される `Fill` ロジックが必要です。 スタンドアロン データ テーブルに格納する方法については、次を参照してください。 [DataAdapter からの Dataset](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)します。  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>新しいスタンドアロンのデータ テーブルを作成するには  
  
1.  データセットを開き、**データセット デザイナー**します。  
  
2.  ドラッグ、<xref:System.Data.DataTable>から、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**します。  
  
3.  列を追加してデータ テーブルを定義します。 詳細については、次を参照してください。[方法: DataTable に列を追加](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataTable>   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [[データ ソース] ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)