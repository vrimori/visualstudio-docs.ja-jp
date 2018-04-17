---
title: XML スキーマ エクスプ ローラー |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84aead3cf496a28e67e6440fb77b8cbf4aca6462
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="xml-schema-explorer"></a>XML スキーマ エクスプローラー
XML スキーマ エクスプローラーは Microsoft Visual Studio および XML エディターに統合されており、これを使用すると、XML スキーマ定義言語 (XSD) スキーマの操作が可能になります。 XML スキーマ ファイルを開くときに、**スキーマ セット**XML スキーマ エクスプ ローラーでノードが表示されます。 XML スキーマ エクスプローラーには、対象ファイルに対してインクルード、インポート、または再定義されたすべてのスキーマだけでなく、`include` ステートメントまたは `import` ステートメントを通じて参照されているファイルも表示されます。  
  
 XML スキーマ エクスプローラーでは、次の操作を実行できます。  
  
-   スキーマ セットの概要をすばやく確認する。  
  
-   ツリーを参照して移動する。  
  
-   キーワード検索とスキーマ固有の検索を実行する。 詳細については、次を参照してください。[スキーマ セットの検索](../xml-tools/searching-the-schema-set.md)です。  
  
-   グラフ ビューまたはコンテンツ モデル ビューに検索結果を追加する。  
  
-   ドキュメントの順序、ドキュメントの種類、またはドキュメント名でツリーを並べ替える。 詳細については、次を参照してください。[並べ替え、フィルター処理、およびグループ化](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)です。  
  
-   XML エディターを開き、XSD ファイルのコードの場所にジャンプする。 詳細については、次を参照してください。 [XML エディターでの統合](../xml-tools/integration-with-xml-editor.md)です。  
  
-   グローバル要素のサンプル XML を生成する。  
  
XML スキーマ エクスプローラーでは、ツリー ビューでスキーマ セットの階層を表示することができます。 また、検索、フィルター処理、ナビゲーション、および並べ替えを行うこともできます。 XML スキーマ エクスプローラーにアクセスするには、次のいずれかの操作を実行します。  
  
-   表示されている場合、[スタート ビュー](../xml-tools/start-view.md)をクリックして、 **XML スキーマ エクスプ ローラー**リンクします。  
  
-   表示されている場合、[グラフ ビュー](../xml-tools/graph-view.md)または[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)ワークスペースにノードがあると、コンテキスト メニューを使用して、XML スキーマ エクスプ ローラーを選択します。  
  
-   XML スキーマ Explorerfrom を選択することも、**ビュー**メニュー。  
  
-   XML スキーマ Explorerfrom を持つ Visual Basic の XML リテラル .xsd ファイルに関連付けられている .vb ファイルにアクセスできます。 スキーマを XML スキーマ エクスプ ローラー設定、XML リテラル内の XML ノードまたは XML 名前空間インポートを右クリックしを選択して、**スキーマ エクスプ ローラーで表示する**コマンド。 詳細については、次を参照してください。[統合の XML リテラルと XML スキーマ エクスプ ローラー](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)です。  
  
## <a name="tree-view"></a>ツリー ビュー  
 XML スキーマ エクスプローラーでは、事前にコンパイルされたスキーマ セット情報がツリー構造で表示されます。 ツリー構造は、次のように構成されます。  
  
-   最上位レベルは、スキーマ セット ノードです。  
  
-   2 番目のレベルには名前空間が含まれます。  
  
-   3 番目のレベルにはファイルが含まれます。  
  
-   4 番目のレベルにはグローバル ノードが含まれます。 これには、要素、グループ、複合型、単純型、属性、属性グループ、`include` ステートメント`import` ステートメント、および `redefine` ステートメントを含めることができます。  
  
ツリー構造の例を次に示します。  
  
![XML スキーマ エクスプ ローラー](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>選択とアクティブ化  
 ノードを強調表示して選択するには、スキーマ エクスプローラーでそのノードをクリックします。  
  
 ノードをアクティブ化、ダブルクリックするか、キーを押して**Enter**ノードを選択するとします。  
  
-   ノードをアクティブ化すると、このノードが定義されているファイルが開き (ファイルが既に開かれていない場合)、ファイル内でノードが選択されます。  
  
-   ファイル ノードをアクティブ化すると、選択されたファイルが開き (既に開かれていない場合)、`<schema>` ノードが強調表示されます。  
  
-   SchemaSet または名前空間ノードをアクティブ化しても、何も行われません。  
  
## <a name="draging-and-dropping-nodes"></a>ノードのドラッグ アンド ドロップ  
 グローバル ノード、ファイル ノード、名前空間ノードを XSD デザイナーのビューにドラッグ アンド ドロップすることができます。 現在のビューがある場合、[スタート ビュー](../xml-tools/start-view.md)が開き、ビューにノードをドラッグして、[グラフ ビュー](../xml-tools/graph-view.md)です。 現在のビューがある場合、[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)またはグラフ ビューの場合、ビューは変化しませんにノードを削除するとします。  
  
 ビュー上のファイルをドロップすると、すべてのグローバル ノードがファイルに追加されます、 [XSD デザイナーのワークスぺース](../xml-tools/xml-schema-designer-workspace.md)です。 ビューに名前空間をドロップすると、名前空間内のすべてのグローバル ノードがワークスぺースに追加されます。 ワークスペースは、すべてのビューで共有されます。  
  
 ローカル ノードまたはローカル インポートをドラッグ アンド ドロップすることはできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [スキーマ セットの検索](../xml-tools/searching-the-schema-set.md)  
  
-   [並べ替え、フィルター、およびグループ化](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [コンテキスト メニュー](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [XML リテラルと XML スキーマ エクスプローラーの統合](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>関連項目  
 [方法: XML スキーマ エクスプローラーからワークスペースにノードを追加する](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)