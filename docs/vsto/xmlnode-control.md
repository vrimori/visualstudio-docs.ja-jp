---
title: "XMLNode コントロール |Microsoft ドキュメント"
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
helpviewer_keywords: XMLNode control
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c35726314dc679289554e24d4150da4294cf8a0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="xmlnode-control"></a>XMLNode コントロール
  **重要な**Microsoft Word に関するこのトピックに設定された情報が、利点と個人ユーザーおよびユーザーは、米国およびその区域外部にあるまたはを使用しているユーザーは、組織の使用専用に示された、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月前に Microsoft によってライセンス供与された Microsoft Word 製品に関連するカスタムの XML から Microsoft Word。 Microsoft Word に関する情報はこの可能性がありますいない読み取りまたは個人または米国またはその区域、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word 製品上で実行されるプログラムの開発を使用して、ユーザーの組織で使用されます。;これらの製品では、その日付の前にライセンスまたは購入し、米国外の利用に対してライセンス供与の製品と同じ動作がしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールは、マップされた XML ノード オブジェクトのイベントを公開し、データにバインドできます。 <xref:Microsoft.Office.Tools.Word.XMLNode>繰り返しのないスキーマ要素は、Microsoft Office Word 文書に対応している場合にのみ、コントロールが作成されます。 Visual Studio では、XML ノードが作成された後は、Word オブジェクト モデルを走査する必要なく、直接に対してプログラミングできます。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールを Word で要素のマッピングを削除することでのみ削除できます。  
  
## <a name="binding-data-to-the-control"></a>コントロールへのデータのバインド  
 <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールは、単純データ バインディングをサポートしています。 XML ノードを使用して、データ ソースにバインドする必要があります、<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>プロパティです。 バインドされたデータセット内のデータが更新された場合、<xref:Microsoft.Office.Tools.Word.XMLNode>コントロールが変更を反映します。  
  
## <a name="formatting"></a>書式設定  
 適用できる書式設定、<xref:Microsoft.Office.Interop.Word.XMLNode>オブジェクトに適用できる、<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 これには、フォント、下線のスタイル、および文字スタイルが含まれます。  
  
## <a name="events"></a>イベント  
 次のイベントは <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールに対して利用できます。  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="comparing-events"></a>イベントの比較  
 ユーザーが特定のコンテキスト内の自分のカーソルを移動したときにイベントをキャプチャする<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 たとえば、する必要があります、<xref:Microsoft.Office.Tools.Word.XMLNode>という名前のコントロール`Customer`子を持つ<xref:Microsoft.Office.Tools.Word.XMLNode>という名前のコントロール`Company`、および`Company`2 つの子を持つ<xref:Microsoft.Office.Tools.Word.XMLNode>という名前のコントロール`CompanyName`と`CompanyRegion`次のように。  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 場合は、[操作] ウィンドウでコントロールを表示するときにカーソルが移動に、`Company`ノード、重要ではありません、カーソルがあるかどうか`CompanyName`または`CompanyRegion`両方のコンテキスト内であるため`Company`です。 この例コードを記述することができます、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>のイベント`Company`です。  
  
 ほとんどの場合、カーソルが入ったときに、<xref:Microsoft.Office.Tools.Word.XMLNode>両方の制御、<xref:Microsoft.Office.Tools.Word.XMLNode.Select>と<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>イベントが発生します。 次の表は、これらのイベント間の相違点を示します。  
  
|イベントを選択します|ContextEnter イベント|  
|------------------|------------------------|  
|カーソルが内に配置するときに発生する<xref:Microsoft.Office.Tools.Word.XMLNode>です。|カーソルが内に配置するときに発生、<xref:Microsoft.Office.Tools.Word.XMLNode>またはノードのコンテキスト外での領域からその子孫のノードのいずれか。 つまり、これは、コンテキストが変更された場合にのみ発生します。|  
  
 などの外部からカーソルを移動する`Customer`に`CompanyName`、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>イベントを`Customer`、 `Company`、および`CompanyName`が発生します。 カーソルを移動する場合`CompanyName`に`CompanyRegion`、のみ、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>イベントを`CompanyRegion`が両方のコンテキストの中であるために発生`Company`と`Customer`です。  
  
 同じの違いがあります、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>イベントと<xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>イベント。  
  
## <a name="see-also"></a>関連項目  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes コントロール](../vsto/xmlnodes-control.md)   
 [方法: Word 文書に XMLNode コントロールを追加します。](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [方法: Visual Studio 内で Word 文書にスキーマをマップ](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  