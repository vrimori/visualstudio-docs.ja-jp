---
title: XMLNode コントロール
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd047814f11b5fddad868bd65b84deba369facd5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258890"
---
# <a name="xmlnode-control"></a>XMLNode コントロール
  **重要な**に関する Microsoft Word には、このトピックでまとめられている情報が提示の特典および個人や組織のユーザーは、米国およびその担当地域外部にあるまたはを使用しているユーザーの使用専用、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月の前に、Microsoft によってライセンスされた Microsoft Word の製品に関連するカスタム XML から Microsoft Word です。 Microsoft Word に関するこの情報が読み取りまたは個人または組織、米国またはその区域を使用して、または、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word の製品で実行されるプログラムの開発で使用しない可能性があります。;これらの製品では、その日付より前にライセンスまたは購入を米国外の使用ライセンスの製品と同じ動作はしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールは、マップされた XML ノード オブジェクトのイベントを公開し、データにバインドすることができます。 <xref:Microsoft.Office.Tools.Word.XMLNode>非繰り返しスキーマ要素が、Microsoft Office Word 文書にマップされている場合にのみコントロールが作成されます。 Visual Studio には、XML ノードが作成されたら、それに対して、Word オブジェクト モデルを走査することがなく直接プログラミングできます。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールを Word で要素のマッピングを削除することによってのみ削除できます。  
  
## <a name="bind-data-to-the-control"></a>データをコントロールにバインドします。  
 <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールは、単純データ バインディングをサポートしています。 XML ノードは、使用してデータ ソースにバインドする必要があります、<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>プロパティ。 バインドされたデータセット内のデータが更新された場合、<xref:Microsoft.Office.Tools.Word.XMLNode>コントロールが変更を反映します。  
  
## <a name="formatting"></a>書式設定  
 適用できる書式設定、<xref:Microsoft.Office.Interop.Word.XMLNode>オブジェクトに適用できる、<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 これには、フォント、下線のスタイル、およびスタイルの文字が含まれます。  
  
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
  
## <a name="compare-events"></a>イベントを比較します。  
 特定のコンテキスト内で自分のカーソルを動かしたときにイベントをキャプチャする<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 たとえば、する必要があります、<xref:Microsoft.Office.Tools.Word.XMLNode>という名前のコントロール`Customer`子を持つ<xref:Microsoft.Office.Tools.Word.XMLNode>という名前のコントロール`Company`、および`Company`が 2 つの子<xref:Microsoft.Office.Tools.Word.XMLNode>という名前のコントロール`CompanyName`と`CompanyRegion`次のように。  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 操作ウィンドウ上のコントロールを表示するたびに、カーソルに移動、`Company`ノード、重要ではありません、カーソルがあるかどうか`CompanyName`または`CompanyRegion`両方のコンテキスト内であるため`Company`します。 この場合でコードを記述することができます、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>のイベント`Company`します。  
  
 ほとんどの場合、カーソルに入ったときに、<xref:Microsoft.Office.Tools.Word.XMLNode>両方の制御、<xref:Microsoft.Office.Tools.Word.XMLNode.Select>と<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>イベントが発生します。 次の表では、これらのイベント間の相違点を示します。  
  
|イベントを選択します。|ContextEnter イベント|  
|------------------|------------------------|  
|カーソルが内に配置するときに発生します、<xref:Microsoft.Office.Tools.Word.XMLNode>します。|カーソルが内に配置するときに発生します、<xref:Microsoft.Office.Tools.Word.XMLNode>またはその子孫のノード、ノードのコンテキスト外からの 1 つ。 つまり、コンテキストが変更された場合にのみ発生します。|  
  
 などの外部からカーソルを移動する`Customer`に`CompanyName`、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>イベントを`Customer`、 `Company`、および`CompanyName`が発生します。 カーソルを移動する場合`CompanyName`に`CompanyRegion`、のみ、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>イベントを`CompanyRegion`が、両方のコンテキストの中であるために発生します`Company`と`Customer`します。  
  
 同じの違いがあります、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>イベントと<xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>イベント。  
  
## <a name="see-also"></a>関連項目  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes コントロール](../vsto/xmlnodes-control.md)   
 [方法: Word 文書に XMLNode コントロールを追加](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [方法: Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  