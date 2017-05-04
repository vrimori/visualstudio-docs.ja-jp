---
title: "XMLNodes コントロール | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "XMLNodes コントロール"
  - "XMLNodes コントロール, イベント"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# XMLNodes コントロール
  **重要** は、マイクロソフトが米国カスタムにある場合や、実行用のプログラム、2010年1月1日の前のMicrosoftによってライセンスMicrosoft Word製品使用している個々の利点のためにMicrosoft Wordに関するこのトピックに記載されているMicrosoft情報がMicrosoft WordからカスタムXMLに関連する特定の機能の実装を削除したときに、使用、および組織。  ここに記載されている Microsoft Word に関する情報を、2010 年 1 月以降にマイクロソフトがライセンスを供与した Microsoft Word 製品上で実行されるプログラムを使用または開発する、米国およびその領土内の個人または組織が参照および使用することはお勧めしません。これに該当する製品は、この日付以前にライセンスが供与された製品、および米国外での使用を目的として購入またはライセンスが供与された製品と同様には動作しません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールは、マップされた XML ノード オブジェクトのコレクションで、イベントを公開しています。  <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールは、繰り返しスキーマ要素が Microsoft Office Word 文書にマップされるときにのみ作成されます。  繰り返し要素に子要素が含まれる場合、各子要素も <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールとして作成されます。  
  
 Visual Studio が XML ノードのコレクションを作成すると、Word オブジェクト モデルを走査せずに、コントロールを直接プログラミングできます。  <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールは、文書から要素のマッピングを削除することによってのみ削除できます。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> プロパティを通じて <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールの子要素にアクセスすると、<xref:Microsoft.Office.Tools.Word.XMLNode> コントロールではなく、<xref:Microsoft.Office.Interop.Word.XMLNode> オブジェクトが返されます。  詳細については、「[ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
## コントロールへのデータのバインド  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールでは、データ バインディングはサポートされません。  これは、<xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールには複合データ バインディング機能がなく、単純データ バインディングでは繰り返しデータを表せないためです。  
  
## 書式設定  
 文書内のテキストに適用できる書式設定は、<xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールにも適用できます。  
  
## イベント  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールで使用できるイベントは次のとおりです。  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## イベントの比較  
 特定の <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールのコンテキスト内でユーザーがポインターを移動したときに、イベントをキャプチャすることができます。  たとえば、`Customer` という名前の <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールがあり、`Company` という名前の子 <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールを持つものとします。`Company` には、次に示すように、`CompanyName` および `CompanyRegion` という名前の、2 つの子 <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールがあります。  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 ポインターが `Company` ノードの内部に移動したときに操作ウィンドウにコントロールを表示する場合、ポインターが `CompanyName` と `CompanyRegion` のどちらの中にあっても違いはありません。両方とも `Company` のコンテキスト内にあるからです。  この場合は、`Company` の <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> イベントにコードを作成できます。  
  
 多くの場合、カーソルが <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールに入ると、<xref:Microsoft.Office.Tools.Word.XMLNodes.Select> および <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> の両イベントが発生します。  この 2 つのイベントの相違点を次の表に示します。  
  
|Select イベント|ContextEnter イベント|  
|-----------------|-----------------------|  
|カーソルが、<xref:Microsoft.Office.Tools.Word.XMLNodes> コレクションのノードの 1 つの内側に置かれると発生します。|カーソルが、ノードのコンテキストの外側の領域から、<xref:Microsoft.Office.Tools.Word.XMLNodes> コレクションのノードの 1 つ、または子孫ノードの内側に置かれると発生します。  つまり、コンテキストが変化する場合にのみ発生し、入れ子になった複数の <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールで発生する可能性があります。|  
  
 たとえば、ポインターを `Customer` の外部から `CompanyName` に移動すると、`Customer`、`Company`、および `CompanyName` で <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> イベントが発生します。  ポインターを `CompanyName` から `CompanyRegion` に移動した場合、`Company` と `Customer` ではコンテキストが同じであるため、`CompanyRegion` でのみ <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> イベントが発生します。  文書内では、複数の `Company` ノードを持つことができます。  ある `Company` の `CompanyName` ノードから別の `Company` の `CompanyName` ノードへポインターを移動した場合、コンテキストが同じであるため、<xref:Microsoft.Office.Tools.Word.XMLNodes.Select> イベントだけが発生します。  
  
 これと同じ違いは、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> イベントと <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> イベントにもあります。  
  
## 参照  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode コントロール](../vsto/xmlnode-control.md)   
 [方法 : Word 文書に XMLNodes コントロールを追加する](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [方法 : Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  