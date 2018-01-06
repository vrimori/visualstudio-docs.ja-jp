---
title: "方法: データベースからデータをドキュメントに読み込む |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b5dcbf99dcc6005c89a7bc67030f2e0f2fddfc5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>方法 : データベースからドキュメントにデータを読み込む
  Microsoft Office のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトでデータにアクセスする場合と同じようにデータにアクセスできます。 同じツールとコードを使用してデータベースからソリューションにデータを読み込むことができ、Windows フォーム コントロールを使用してデータを表示できます。  
  
 また、ホスト コントロールを使用してデータを表示することもできます。 ホスト コントロールは、イベントおよびデータ バインディングの機能が強化された Microsoft Office Word のネイティブ オブジェクトです。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 次の例は、デザイナーを使用してドキュメント レベルのプロジェクトにデータ バインド コントロールを追加する方法を示しています。 実行時に VSTO アドイン プロジェクトでのデータ バインド コントロールを追加する方法の例は、次を参照してください。[チュートリアル: VSTO での単純データ バインディング アドイン プロジェクト](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)です。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [Word 2007 コンテンツ コントロールを使用して Visual Studio Tools for the Office System (3.0) へのデータ バインディング](http://go.microsoft.com/fwlink/?LinkId=136785)です。  
  
## <a name="adding-a-control-to-a-document-at-design-time"></a>デザイン時にドキュメントにコントロールを追加する  
  
#### <a name="to-populate-a-document-with-data-from-a-database"></a>データベースからドキュメントにデータを読み込むには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で Word のドキュメント レベルのプロジェクトを開き、ドキュメントをデザイナーで開きます。  
  
2.  開く、**データソース**ウィンドウ データベースからデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)です。  
  
3.  目的のフィールドをドラッグして、**データ ソース**ウィンドウをドキュメントにします。  
  
 コンテンツ コントロールが文書に追加されます。 コンテンツ コントロールの種類は、選択したフィールドのデータ型によって異なります。 詳細については、「 [Content Controls](../vsto/content-controls.md)」を参照してください。  
  
 データ フィールドを選択して別のコントロールを追加することができます、**データソース**ウィンドウとドロップダウン リストから別のコントロールを選択します。  
  
## <a name="objects-in-the-project"></a>プロジェクト内のオブジェクト  
 プロジェクトには、コントロールに加えて、データに関連する以下のオブジェクトも自動的に追加されます。  
  
-   データベース内の接続したデータ テーブルをカプセル化する型指定されたデータセット。 詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](/visualstudio/data-tools/dataset-tools-in-visual-studio)です。  
  
-   コントロールを型指定されたデータセットに接続する <xref:System.Windows.Forms.BindingSource>。 詳細については、「 [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview)」を参照してください。  
  
-   型指定されたデータセットをデータベースに接続する TableAdapter。 詳細については、次を参照してください。[作成し、Tableadapter を構成](../data-tools/create-and-configure-tableadapters.md)です。  
  
-   TableAdapterManager、階層更新を有効にする、データセット内のテーブル アダプターを調整するために使用します。 詳細については、次を参照してください。[階層更新](../data-tools/hierarchical-update.md)と[TableAdapterManager 参照](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)です。  
  
 プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。 <xref:System.Windows.Forms.BindingSource> を使用すると、ユーザーがレコードをスクロールできるようになります。  
  
#### <a name="to-scroll-through-the-records"></a>レコードをスクロールするには  
  
-   <xref:System.Windows.Forms.BindingSource.MoveNext%2A> や <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> など、<xref:System.Windows.Forms.BindingSource> のメソッドを使用します。  
  
 型指定されたデータセットと、データベースに更新を送信する方法については、次を参照してください。[する方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)です。  
  
## <a name="see-also"></a>参照  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [新しいデータ ソースを追加します。](/visualstudio/data-tools/add-new-data-sources)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office ソリューションの概要にあるローカル データベース ファイルを使用します。](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Windows フォーム アプリケーションのデータへの接続](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  