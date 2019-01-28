---
title: Visio オブジェクト モデルの概要
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbdcecc11a260130128c60c222da10c249a58799
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869324"
---
# <a name="visio-object-model-overview"></a>Visio オブジェクト モデルの概要
  Visio オブジェクト モデルと対話することにより、Microsoft Office Visio 用の Office ソリューションを開発できます。 このオブジェクト モデルは、Visio のプライマリ相互運用機能アセンブリで提供されるクラスとインターフェイスで構成されています。それらは `Microsoft.Office.Interop.Visio` 名前空間の中で定義されています。  
  
 ここでは、Visio オブジェクト モデルの概要を簡単に説明します。 Office プロジェクトでタスクを実行するために Visio オブジェクト モデルを使用する方法については、次のトピックを参照してください。  
  
-   [Visio 図面の操作します。](../vsto/working-with-visio-documents.md)  
  
-   [Visio 図形を操作します。](../vsto/working-with-visio-shapes.md)  
  
## <a name="understand-the-visio-object-model"></a>Visio オブジェクト モデルを理解します。  
 Visio では、多くのオブジェクトが操作対象になります。 これらのオブジェクトは、ユーザー インターフェイスとほぼ同様の階層形式で編成されています。 階層の最上位にあるのは、 [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) オブジェクトです。 このオブジェクトは、Visio の現在のインスタンスを表します。 `Microsoft.Office.Interop.Visio.Application`オブジェクトが含まれています、`Microsoft.Office.Interop.Visio.Document`と`Microsoft.Office.Interop.Visio.Page`オブジェクトだけでなく`Microsoft.Office.Interop.Visio.Documents`と`Microsoft.Office.Interop.Visio.Pages`コレクション。 これらのオブジェクトとコレクションにはそれぞれ数多くのメソッドとプロパティがあり、それらにアクセスしてオブジェクトを処理したり、オブジェクトと対話したりできます。  
  
 詳細については、 [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application)、 [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)、および [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) の各オブジェクト、 [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) および [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) の各コレクションの VBA リファレンス ドキュメントを参照してください。  
  
 この後のセクションでは、最上位レベルのオブジェクトとそれらの相互関係について、簡単に説明します。 このようなオブジェクトには次の 4 つがあります。  
  
-   Application オブジェクト  
  
-   Document オブジェクト  
  
-   Page オブジェクト  
  
### <a name="application-object"></a>Application オブジェクト  
 Microsoft.Office.Interop.Visio.Application オブジェクトは、Visio アプリケーションを表し、すべての他のオブジェクトの親であります。 そのメンバーは、通常、Visio 全体に適用されます。 プロパティと、Microsoft.Office.Interop.Visio.Application のメソッドを使用して、 `Microsoft.Office.Interop.Visio.ApplicationSettings` Visio の環境を制御するオブジェクト。  
  
 VSTO アドイン プロジェクトを使用して Microsoft.Office.Interop.Visio.Application オブジェクトにアクセスすることができます、`Application`のフィールド、`ThisAddIn`クラス。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
### <a name="document-object"></a>Document オブジェクト  
 Microsoft.Office.Interop.Visio.Document オブジェクトは、Visio プログラミングの中心となります。 これは、図面、ステンシル、またはテンプレート ファイルを表します。 Microsoft.Office.Interop.Visio.Application オブジェクトの Microsoft.Office.Interop.Visio.Documents コレクションに追加される新しい Microsoft.Office.Interop.Visio.Document オブジェクトを作成する Visio 図面を開くまたは新しいドキュメントを作成するときに.  
  
 フォーカスがある文書は、作業中の文書と呼ばれます。 これによって表されますが、 `Microsoft.Office.Interop.Visio.Application.ActiveDocument` Microsoft.Office.Interop.Visio.Application オブジェクトのプロパティ。  
  
### <a name="page-object"></a>Page オブジェクト  
 Microsoft.Office.Interop.Visio.Page オブジェクトは、フォア グラウンドまたはバック グラウンドのページの描画領域を表します。 `Microsoft.Office.Interop.Visio.Page.Background` プロパティを使用すると、ページが前景ページと背景ページのどちらであるかを判定できます。  
  
 図形を作成するには、`Microsoft.Office.Interop.Visio.Page.DrawSpline` メソッドや `Microsoft.Office.Interop.Visio.Page.DrawOval` メソッドなどのメソッドを使用できます。 さらに、ステンシルからマスターを取得し、`Microsoft.Office.Interop.Visio.Page.Drop` メソッドまたは `Microsoft.Office.Interop.Visio.Page.DropMany` メソッドを使用することにより図形をページに配置できます。  
  
## <a name="use-the-visio-object-model-documentation"></a>Visio オブジェクト モデル ドキュメントを使用します。  
 Visio オブジェクト モデルの詳細については、Visio の VBA オブジェクト モデルのリファレンスを参照してください。 VBA オブジェクト モデルのリファレンス ドキュメントでは、Visual Basic for Applications (VBA) コードに公開される Visio オブジェクト モデルについて説明しています。 詳細については、次を参照してください。 [Visio 2010 オブジェクト モデル リファレンス](http://go.microsoft.com/fwlink/?LinkId=199775)します。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Visio プライマリ相互運用機能アセンブリ (PIA) の型とメンバーに対応します。 たとえば、 `Document` VBA オブジェクト モデルのリファレンス内のオブジェクトが、Visio pia Microsoft.Office.Interop.Visio.Document 型に対応します。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Visio VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
> [!NOTE]  
>  現在のところ、Visio プライマリ相互運用機能アセンブリに関するリファレンス ドキュメントは提供されていません。  
  
 Visio ソリューションを作成するための他のツールと関連するコード例は、次を参照してください。 [Visio 2010 ソフトウェア開発キット](http://go.microsoft.com/fwlink/?LinkId=196501)します。  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>プライマリ相互運用機能アセンブリの追加の型  
 実装の違いにより VBA には表示されないプライマリ相互運用機能アセンブリの型があります。 VBA では、直接使用できるオブジェクトとメンバーだけを含む Visio オブジェクト モデルのビューが提供されます。 プライマリ相互運用機能アセンブリは同じオブジェクト モデルを公開しますが、それには、COM オブジェクト モデルのオブジェクトをマネージド コードに変換する、その他のインターフェイス、クラス、およびメンバーも含まれています。 これらの追加の項目は、コードで直接使用するためのものではありません。  
  
 詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio 図面の操作します。](../vsto/working-with-visio-documents.md)   
 [Visio 図形を操作します。](../vsto/working-with-visio-shapes.md)  
