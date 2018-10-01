---
title: XML スキーマ エクスプ ローラー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6fe09ca80bd9a5f4d94942adcfd98c139acdc6c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536645"
---
# <a name="xml-schema-explorer"></a>XML スキーマ エクスプローラー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[XML スキーマ エクスプ ローラー](https://docs.microsoft.com/visualstudio/xml-tools/xml-schema-explorer)します。  
  
  
XML スキーマ エクスプローラーは Microsoft Visual Studio および XML エディターに統合されており、これを使用すると、XML スキーマ定義言語 (XSD) スキーマの操作が可能になります。 XML スキーマ ファイルを開くと、**スキーマ セット**XML スキーマ エクスプ ローラーでノードが表示されます。 XML スキーマ エクスプローラーには、対象ファイルに対してインクルード、インポート、または再定義されたすべてのスキーマだけでなく、`include` ステートメントまたは `import` ステートメントを通じて参照されているファイルも表示されます。  
  
 XML スキーマ エクスプローラーでは、次の操作を実行できます。  
  
-   スキーマ セットの概要をすばやく確認する。  
  
-   ツリーを参照して移動する。  
  
-   キーワード検索とスキーマ固有の検索を実行する。 詳細については、次を参照してください。[スキーマ セットの検索](../xml-tools/searching-the-schema-set.md)します。  
  
-   グラフ ビューまたはコンテンツ モデル ビューに検索結果を追加する。  
  
-   ドキュメントの順序、ドキュメントの種類、またはドキュメント名でツリーを並べ替える。 詳細については、次を参照してください。[並べ替え、フィルター処理、およびグループ化](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)します。  
  
-   XML エディターを開き、XSD ファイルのコードの場所にジャンプする。 詳細については、次を参照してください。 [XML エディターとの統合](../xml-tools/integration-with-xml-editor.md)します。  
  
-   グローバル要素のサンプル XML を生成する。  
  
 XML スキーマ エクスプローラーでは、ツリー ビューでスキーマ セットの階層を表示することができます。 また、検索、フィルター処理、ナビゲーション、および並べ替えを行うこともできます。 XML スキーマ エクスプローラーにアクセスするには、次のいずれかの操作を実行します。  
  
-   使用している場合、[スタート ビュー](../xml-tools/start-view.md)、クリックして、 **XML スキーマ エクスプ ローラー**リンク。  
  
-   使用している場合、[グラフ ビュー](../xml-tools/graph-view.md)または[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)ワークスペースにノードがあるとは、コンテキスト メニューを使用して、XML スキーマ エクスプ ローラーを選択します。  
  
-   XML スキーマの Explorerfrom を選択することも、**ビュー**メニュー。  
  
-   XML スキーマ Explorerfrom を Visual Basic の XML リテラルに関連付けられた .xsd ファイルを持つ .vb ファイルにアクセスできます。 XML スキーマ エクスプ ローラーの設定、XML リテラル内の XML ノードまたは XML 名前空間インポートを右クリックし、選択のスキーマを表示する、**スキーマ エクスプ ローラーで表示する**コマンド。 詳細については、次を参照してください。 [XML スキーマ エクスプ ローラーを使用した XML リテラルの統合](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)します。  
  
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
  
 ノードをアクティブ化をダブルクリックするか、キーを押します**Enter**ノードを選択するとします。  
  
-   ノードをアクティブ化すると、このノードが定義されているファイルが開き (ファイルが既に開かれていない場合)、ファイル内でノードが選択されます。  
  
-   ファイル ノードをアクティブ化すると、選択されたファイルが開き (既に開かれていない場合)、`<schema>` ノードが強調表示されます。  
  
-   SchemaSet または名前空間ノードをアクティブ化しても、何も行われません。  
  
## <a name="draging-and-dropping-nodes"></a>ノードのドラッグ アンド ドロップ  
 グローバル ノード、ファイル ノード、名前空間ノードを XSD デザイナーのビューにドラッグ アンド ドロップすることができます。 現在のビューがある場合、[スタート ビュー](../xml-tools/start-view.md)、ビューにノードのドラッグが開き、[グラフ ビュー](../xml-tools/graph-view.md)。 現在のビューがある場合、[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)またはグラフ ビュー、ビューは変更されませんにノードを削除するとします。  
  
 ファイルにすべてのグローバル ノードを追加、ビュー上のファイルを削除するが、 [XSD デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)します。 ビューに名前空間をドロップすると、名前空間内のすべてのグローバル ノードがワークスぺースに追加されます。 ワークスペースは、すべてのビューで共有されます。  
  
 ローカル ノードまたはローカル インポートをドラッグ アンド ドロップすることはできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [スキーマ セットの検索](../xml-tools/searching-the-schema-set.md)  
  
-   [並べ替え、フィルター処理、およびグループ化](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [コンテキスト メニュー](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [XML リテラルと XML スキーマ エクスプローラーの統合](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>関連項目  
 [方法: XML スキーマ エクスプローラーからワークスペースにノードを追加する](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)







