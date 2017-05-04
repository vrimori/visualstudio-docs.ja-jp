---
title: "XMLNode コントロール | Microsoft Docs"
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
  - "XMLNode コントロール"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# XMLNode コントロール
  **重要** は、マイクロソフトが米国カスタムにある場合や、実行用のプログラム、2010年1月1日の前のMicrosoftによってライセンスMicrosoft Word製品使用している個々の利点のためにMicrosoft Wordに関するこのトピックに記載されているMicrosoft情報がMicrosoft WordからカスタムXMLに関連する特定の機能の実装を削除したときに、使用、および組織。  ここに記載されている Microsoft Word に関する情報を、2010 年 1 月以降にマイクロソフトがライセンスを供与した Microsoft Word 製品上で実行されるプログラムを使用または開発する、米国およびその領土内の個人または組織が参照および使用することはお勧めしません。これに該当する製品は、この日付以前にライセンスが供与された製品、および米国外での使用を目的として購入またはライセンスが供与された製品と同様には動作しません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールは、イベントを公開する、割り当てられた XML ノード オブジェクトであり、データに結合できます。  <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールは、非繰り返しスキーマ要素が Microsoft Office Word 文書にマップされたときにのみ作成されます。  Visual Studio で XML ノードが作成された後、このノードは、Word オブジェクト モデルを走査しなくても、コードで直接使用できます。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールは、Word 内の要素のマッピングを削除することによってのみ削除できます。  
  
## コントロールへのデータのバインド  
 <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールは、単純データ バインディングをサポートしています。  XML ノードをデータ ソースにバインドするには、<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> プロパティを使用する必要があります。  バインドされたデータセット内のデータが更新された場合は、その変更が <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールに反映されます。  
  
## 書式設定  
 <xref:Microsoft.Office.Interop.Word.XMLNode> オブジェクトに適用できる書式設定を <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールに適用できます。  フォント、下線のスタイル、文字スタイルなどを設定できます。  
  
## イベント  
 次のイベントは <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールで使用できます。  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## イベントの比較  
 特定の <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールのコンテキスト内でユーザーがポインターを移動したときに、イベントをキャプチャすることができます。  たとえば、次のように `Customer` という名前の <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールに `Company` という名前の子 <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールがあり、`Company` には `CompanyName` および `CompanyRegion` という名前の 2 つの子 <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールがあるとします。  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 ポインターが `Company` ノードの内部に移動したときに操作ウィンドウにコントロールを表示する場合、ポインターが `CompanyName` と `CompanyRegion` のどちらの中にあっても違いはありません。両方とも `Company` のコンテキスト内にあるからです。  この場合、`Company` の <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> イベントにコードを書くことができます。  
  
 ほとんどの場合、ポインターが <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールの内部に移動すると、<xref:Microsoft.Office.Tools.Word.XMLNode.Select> イベントと <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> イベントの両方が発生します。  これらのイベントの相違点を次の表に示します。  
  
|Select イベント|ContextEnter イベント|  
|-----------------|-----------------------|  
|ポインターが <xref:Microsoft.Office.Tools.Word.XMLNode> の内部に配置されたときに発生します。|ポインターが <xref:Microsoft.Office.Tools.Word.XMLNode> またはその子孫ノードの内部に、ノードのコンテキスト外から配置されたときに発生します。  つまり、コンテキストが変わったときにのみ発生します。|  
  
 たとえば、ポインターを `Customer` の外部から `CompanyName` に移動すると、`Customer`、`Company`、および `CompanyName` で <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> イベントが発生します。  ポインターを `CompanyName` から `CompanyRegion` に移動した場合、ポインターは `Company` と `Customer` の 両方のコンテキスト内にまだあるので、`CompanyRegion` の <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> イベントのみが発生します。  
  
 これと同じ違いは、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> イベントと <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> イベントにもあります。  
  
## 参照  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes コントロール](../vsto/xmlnodes-control.md)   
 [方法 : Word 文書に XMLNode コントロールを追加する](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [方法 : Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  