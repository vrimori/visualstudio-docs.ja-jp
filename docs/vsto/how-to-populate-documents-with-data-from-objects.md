---
title: "方法: オブジェクトからのデータをドキュメントに読み込む |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 418e56c83a463c10d9dfc990236315751e07c000
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>方法 : オブジェクトのデータをドキュメントに読み込む
  Microsoft Office Word のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトと同じ方法でデータ オブジェクトのデータにアクセスできます。 同じツールとコードを使用してオブジェクトからソリューションにデータを読み込むことができ、Windows フォーム コントロールを使用してデータを表示できます。 また、ホスト コントロールを使用してデータを表示することもできます。 ホスト コントロールは、イベントおよびデータ バインディングの機能が強化された Microsoft Office Word のネイティブ オブジェクトです。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 ドキュメントにオブジェクトのデータを読み込むには、次の 3 つの基本手順を実行する必要があります。  
  
-   データにバインドできるドキュメントにコントロールを追加する。  
  
-   データ オブジェクトをドキュメントに追加する。  
  
-   データ オブジェクトを BindingSource に接続する。   
  
## <a name="adding-a-data-object"></a>データ オブジェクトの追加  
  
#### <a name="to-add-a-data-object"></a>データ オブジェクトを追加するには  
  
-   **[データ ソース]** ウィンドウを開き、オブジェクトからデータ ソースを作成します。 詳細については、「[新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)」を参照してください。  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>データ オブジェクトの BindingSource への接続  
 ドキュメント レベルのプロジェクトでは、デザイン時にコントロールを文書に追加し、そのコントロールをデータにバインドできます。  
  
 VSTO アドイン プロジェクトでは、コントロールを作成して、そのコントロールを実行時にバインドできます。  
  
### <a name="document-level-projects"></a>ドキュメント レベルのプロジェクト  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>データ オブジェクトを BindingSource に接続するには  
  
1.  **[データ ソース]** ウィンドウから目的のデータ フィールドを文書にドラッグします これにより、コントロールが自動的に作成されます。  
  
2.  コードで、データ ソースとして選択したオブジェクトの種類のインスタンスを作成します。  
  
3.  このインスタンスを <xref:System.Windows.Forms.BindingSource.DataSource%2A> の <xref:System.Windows.Forms.BindingSource>プロパティに割り当てます。  
  
### <a name="application-level-projects"></a>アプリケーション レベルのプロジェクト  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>データ オブジェクトを BindingSource に接続するには  
  
1.  コード中に、データ ソースに関連付けられているオブジェクトの種類のインスタンスを作成します。  
  
2.  <xref:System.Windows.Forms.BindingSource>のインスタンスを作成します。  
  
3.  データ ソースのインスタンスを <xref:System.Windows.Forms.BindingSource.DataSource%2A> の <xref:System.Windows.Forms.BindingSource>プロパティに割り当てます。  
  
4.  コントロールへのデータ バインディングとしてデータ ソースを追加します。  
  
## <a name="see-also"></a>関連項目  
 
 [新しいデータ ソースを追加します。](/visualstudio/data-tools/add-new-data-sources)   
 [Windows フォーム コントロールでデータをバインド Visual Stduio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Windows フォーム アプリケーションのデータへの接続](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  