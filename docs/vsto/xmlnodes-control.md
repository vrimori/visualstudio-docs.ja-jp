---
title: XMLNodes コントロール
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18b1a9cf6028b02d16b15b17950b9918b7b79d89
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258539"
---
# <a name="xmlnodes-control"></a>XMLNodes コントロール
  **重要な**に関する Microsoft Word には、このトピックでまとめられている情報が提示の特典および個人や組織のユーザーは、米国およびその担当地域外部にあるまたはを使用しているユーザーの使用専用、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月の前に、Microsoft によってライセンスされた Microsoft Word の製品に関連するカスタム XML から Microsoft Word です。 Microsoft Word に関するこの情報が読み取りまたは個人または組織、米国またはその区域を使用して、または、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word の製品で実行されるプログラムの開発で使用しない可能性があります。;これらの製品では、その日付より前にライセンスまたは購入を米国外の使用ライセンスの製品と同じ動作はしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールは、イベントを公開するマップされた XML ノード オブジェクトのコレクション。 <xref:Microsoft.Office.Tools.Word.XMLNodes>繰り返されるスキーマ要素が、Microsoft Office Word 文書にマップされている場合にのみコントロールが作成されます。 としても作成の各子要素が、反復される要素に子要素が含まれている場合、<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール。  
  
 Visual Studio では、XML ノードのコレクションが作成された後、Word オブジェクト モデルを走査することがなく直接コントロールに対してプログラミングできます。 <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールをドキュメントから要素のマッピングを削除することによってのみ削除できます。  
  
> [!NOTE]  
>  子要素にアクセスする場合、<xref:Microsoft.Office.Tools.Word.XMLNodes>を介して制御、<xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>プロパティを取得、<xref:Microsoft.Office.Interop.Word.XMLNode>オブジェクトではなく<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 詳細については、次を参照してください。[ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)します。  
  
## <a name="bind-data-to-the-control"></a>データをコントロールにバインドします。  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールがデータ バインディングをサポートしていません。 これは、ため、<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールにバインディング機能、複雑なデータがないと、単純データ バインディングを表すことはできません繰り返しデータ。  
  
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
  
## <a name="compare-events"></a>イベントを比較します。  
 特定のコンテキスト内で自分のカーソルを動かしたときにイベントをキャプチャする<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール。 たとえば、する必要があります、<xref:Microsoft.Office.Tools.Word.XMLNodes>という名前のコントロール`Customer`子を持つ<xref:Microsoft.Office.Tools.Word.XMLNodes>という名前のコントロール`Company`、および`Company`が 2 つの子<xref:Microsoft.Office.Tools.Word.XMLNodes>という名前のコントロール`CompanyName`と`CompanyRegion`次のように。  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 操作ウィンドウ上のコントロールを表示するたびに、カーソルに移動、`Company`ノード、重要ではありません、カーソルがあるかどうか`CompanyName`または`CompanyRegion`両方のコンテキスト内であるため`Company`します。 この場合でコードを記述することができます、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>のイベント`Company`します。  
  
 ほとんどの場合、カーソルに入ったときに、<xref:Microsoft.Office.Tools.Word.XMLNodes>両方の制御、<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>と<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>イベントが発生します。 次の表では、これらのイベント間の違いを示します。  
  
|イベントを選択します。|ContextEnter イベント|  
|------------------|------------------------|  
|カーソルがいずれかのノード内に配置するときに発生します、<xref:Microsoft.Office.Tools.Word.XMLNodes>コレクション。|カーソルがノードの子孫ノードのいずれかの内側に配置するときに発生します、<xref:Microsoft.Office.Tools.Word.XMLNodes>ノードのコンテキスト外からのコレクション。 つまり、コンテキストが変更されたときにのみ発生した入れ子になった複数の発生する可能性と<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール。|  
  
 などの外部からカーソルを移動する`Customer`に`CompanyName`、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>イベント`Customer`、 `Company`、および`CompanyName`が発生します。 カーソルを移動する場合`CompanyName`に`CompanyRegion`、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>イベントのみを`CompanyRegion`コンテキストが両方に同じであるため、発生`Company`と`Customer`します。 複数`Company`ドキュメント内のノード。 カーソルを移動する場合、`CompanyName`ノードの 1 つ`Company`を`CompanyName`別のノード`Company`、コンテキストが同じでのみ、<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>イベントが発生します。  
  
 同じの違いがあります、<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>イベントと<xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>イベント。  
  
## <a name="see-also"></a>関連項目  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode コントロール](../vsto/xmlnode-control.md)   
 [方法: Word 文書に XMLNodes コントロールを追加](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [方法: Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  