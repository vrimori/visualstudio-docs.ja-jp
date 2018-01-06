---
title: "XMLNodes コントロール |Microsoft ドキュメント"
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
- XMLNodes control, events
- XMLNodes control
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e59fb1ee6f3f8ea0be474f6fffabdc2c4ef7510e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xmlnodes-control"></a>XMLNodes コントロール
  **重要な**Microsoft Word に関するこのトピックに設定された情報が、利点と個人ユーザーおよびユーザーは、米国およびその区域外部にあるまたはを使用しているユーザーは、組織の使用専用に示された、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月前に Microsoft によってライセンス供与された Microsoft Word 製品に関連するカスタムの XML から Microsoft Word。 Microsoft Word に関する情報はこの可能性がありますいない読み取りまたは個人または米国またはその区域、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word 製品上で実行されるプログラムの開発を使用して、ユーザーの組織で使用されます。;これらの製品では、その日付の前にライセンスまたは購入し、米国外の利用に対してライセンス供与の製品と同じ動作がしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールは、マップされた XML ノードのオブジェクトのコレクションであり、イベントを公開します。 <xref:Microsoft.Office.Tools.Word.XMLNodes>繰り返されるスキーマ要素は、Microsoft Office Word 文書に対応している場合にのみ、コントロールが作成されます。 としても作成、子要素の各反復される要素の子要素が含まれている場合、<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール。  
  
 Visual Studio では、XML ノードのコレクションが作成された後は、Word オブジェクト モデルを走査する必要なく、直接コントロールに対してプログラミングできます。 <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールをドキュメントから要素のマッピングを削除することでのみ削除できます。  
  
> [!NOTE]  
>  子要素にアクセスする場合、<xref:Microsoft.Office.Tools.Word.XMLNodes>を介して制御、<xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>プロパティが返されます、<xref:Microsoft.Office.Interop.Word.XMLNode>オブジェクトではなく、<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 詳細については、「 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
## <a name="binding-data-to-the-control"></a>コントロールへのデータのバインド  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールがデータ バインディングをサポートしていません。 これは、ため、<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールにバインディングの機能、複雑なデータがないと、単純データ バインディングが表すことができないデータを繰り返しです。  
  
## <a name="formatting"></a>書式設定  
 ドキュメント内のテキストに適用できる書式設定を適用できる、<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール。  
  
## <a name="events"></a>イベント  
 利用可能なイベント、<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールは。  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>イベントの比較  
 ユーザーが特定のコンテキスト内の自分のカーソルを移動したときにイベントをキャプチャする<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール。 たとえば、する必要があります、<xref:Microsoft.Office.Tools.Word.XMLNodes>という名前のコントロール`Customer`子を持つ<xref:Microsoft.Office.Tools.Word.XMLNodes>という名前のコントロール`Company`、および`Company`2 つの子を持つ<xref:Microsoft.Office.Tools.Word.XMLNodes>という名前のコントロール`CompanyName`と`CompanyRegion`次のように。  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 場合は、[操作] ウィンドウでコントロールを表示するときにカーソルが移動に、`Company`ノード、重要ではありません、カーソルがあるかどうか`CompanyName`または`CompanyRegion`両方のコンテキスト内であるため`Company`です。 この例コードを記述することができます、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>のイベント`Company`です。  
  
 ほとんどの場合、カーソルが入ったときに、<xref:Microsoft.Office.Tools.Word.XMLNodes>両方の制御、<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>と<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>イベントが発生します。 次の表は、これらのイベント間の相違点を示します。  
  
|イベントを選択します|ContextEnter イベント|  
|------------------|------------------------|  
|内のノードのいずれかのカーソルを配置しているときに発生、<xref:Microsoft.Office.Tools.Word.XMLNodes>コレクション。|カーソルがノードの子孫ノードのいずれかの内側にある場合に発生、<xref:Microsoft.Office.Tools.Word.XMLNodes>ノードのコンテキスト外での領域からのコレクション。 つまり、これは、コンテキストが変更されたときにのみ、入れ子になった複数発生する可能性と<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール。|  
  
 などの外部からカーソルを移動する`Customer`に`CompanyName`、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>イベントを`Customer`、 `Company`、および`CompanyName`が発生します。 カーソルを移動する場合`CompanyName`に`CompanyRegion`、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>イベントのみを`CompanyRegion`が発生すると、コンテキストがの両方で同じであるため`Company`と`Customer`です。 複数`Company`ドキュメント内のノードです。 カーソルを移動する場合、`CompanyName`ノードの 1 つ`Company`を`CompanyName`別のノード`Company`、コンテキストは、同じで、のみ、<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>イベントが発生します。  
  
 同じの違いがあります、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>イベントおよび<xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>イベント。  
  
## <a name="see-also"></a>参照  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode コントロール](../vsto/xmlnode-control.md)   
 [方法: Word 文書に XMLNodes コントロールを追加します。](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [方法: Visual Studio 内で Word 文書にスキーマをマップ](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  