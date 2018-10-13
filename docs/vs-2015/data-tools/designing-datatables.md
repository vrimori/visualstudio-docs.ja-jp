---
title: Datatable のデザイン |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vbdata.Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- tables [Visual Studio]
- data [Visual Studio], designing DataTables
- DataTable objects
ms.assetid: 17014125-ab28-45ec-8789-01b6fc9a8e6a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e7ff3bde70fb45f28bac10d5191bcc6fe3dc8afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213708"
---
# <a name="designing-datatables"></a>DataTable のデザイン
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] デザイン時ツールを作成して、データ テーブルの編集を提供します (**DataTable**)。 内容の概要については、 **DataTable**を参照してください[Datatable](http://msdn.microsoft.com/library/52ff0e32-3e5a-41de-9a3b-7b04ea52b83e)します。  
  
 次のトピックでは、データ テーブルを作成を使用して型指定されたデータセットに追加する方法、**データセット デザイナー**を作成し、データ列の編集 (**DataColumn**) それらを定義します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: データ テーブルを作成する](../data-tools/how-to-create-data-tables.md)  
 新たに作成する手順を説明<xref:System.Data.DataTable>で、**データセット デザイナー**します。  
  
 [方法: DataTable に列を追加](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)  
 新たに作成する手順を説明<xref:System.Data.DataColumn>既存の<xref:System.Data.DataTable>します。  
  
 [チュートリアル : データセット デザイナーでの DataTable の作成](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)  
 作成するための手順について説明します、<xref:System.Data.DataTable>を定義して、<xref:System.Data.DataColumn>その構造を構成します。  
  
## <a name="reference"></a>参照  
 <xref:System.Data.DataSet>  
 データのメモリ内キャッシュを表します。  
  
 <xref:System.Data.DataTable>  
 メモリ内データの 1 つのテーブルを表します。  
  
 <xref:System.Data.DataColumn>  
 内の列のスキーマを表す、<xref:System.Data.DataTable>します。  
  
 <xref:System.Data.DataRelation>  
 2 つの親/子リレーションシップを表す<xref:System.Data.DataTable>オブジェクト。  
  
## <a name="related-sections"></a>関連項目  
 [DataTables](http://msdn.microsoft.com/library/52ff0e32-3e5a-41de-9a3b-7b04ea52b83e)  
 作成およびカスタマイズする方法について説明します`DataTable`オブジェクト。  
  
 [Tableadapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)  
 作成し、デザイン時ツールで Tableadapter を編集する方法を説明するトピックへのリンクを示します。  
  
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)  
 Visual Studio でのデータに接続するさまざまな方法を説明するトピックへのリンクを示します。  
  
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 データセットは、新しいデータセットを作成する方法、および作成および構成する個々 のオブジェクトを編集する方法を説明するトピックへのリンクを提供します。  
  
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)  
 クエリとストアド プロシージャを実行して、データセットにデータを読み込む方法を説明するトピックへのリンクを提供します。  
  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 データ バインド コントロールを Windows フォームにデータを表示する方法を説明するトピックへのリンクを提供します。  
  
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)  
 データセット内のデータの操作を説明するトピックへのリンクを示します。  
  
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 データを検証するコードを配置する場所を説明するトピックへのリンクを提供します。  
  
 [データの保存](../data-tools/saving-data.md)  
 アプリケーションからデータベースに更新されたデータを送信する方法を説明するトピックへのリンクを提供します。