---
title: Office プロジェクトのプロパティ
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2b5c5e0719f7b619fa00a3a0f4333ae0080c0715
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692773"
---
# <a name="properties-in-office-projects"></a>Office プロジェクトのプロパティ
  Visual Studio で Office プロジェクトに使用できる重要なプロパティがいくつかあります。 これらのプロパティには **[プロパティ]** ウィンドウでアクセスできます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>ホスト項目の Namespace  
 Visual C# プロジェクトでホスト項目クラス (たとえば、 **、** 、 `ThisAddIn`クラス) の名前空間を変更するには、[ `ThisWorkbook`ホスト項目の名前空間 `ThisDocument` ] プロパティを使用します。 このプロパティに表示されて、**プロパティ**ウィンドウ、ドキュメント レベルのプロジェクトで、[ドキュメント] ノードを選択すると (など*ExcelWorkbook1.xlsx*または*worddocument1.docx など*) または (Excel や Word など) には VSTO アドイン プロジェクトでのアプリケーション ノード**ソリューション エクスプ ローラー**です。  
  
 Visual C# Office プロジェクトを作成すると、プロジェクトの名前に基づいてホスト項目に名前空間が与えられます。 コード ファイルを直接編集するのではなく、**[ホスト項目の名前空間]** プロパティを使用して名前空間を変更することをお勧めします。 このプロパティを使用すると、名前空間は、生成されるコード ファイル (非表示) だけでなく、表示されるコード ファイル内でも変更されます。  
  
## <a name="cacheindocument"></a>CacheInDocument  
 **CacheInDocument** プロパティは、Visual Studio デザイナーで **のインスタンスを選択すると、ドキュメント レベルのプロジェクトの [** プロパティ <xref:System.Data.DataSet> ] ウィンドウに表示されます。 パブリック メンバーだけがキャッシュされます。 **をキャッシュする場合は、[** Modifiers **] プロパティを [** Public <xref:System.Data.DataSet>] に設定してください。  
  
 このプロパティはブール値を受け取ります。  
  
-   ドキュメント内のデータセットをキャッシュする場合は、 **true** を選択します。  
  
-   ドキュメントのデータセットをキャッシュしない場合は、 **false** を選択します。  
  
 データのキャッシュの詳細については、次を参照してください。[ドキュメント レベルのカスタマイズでキャッシュされたデータ](../vsto/cached-data-in-document-level-customizations.md)です。  
  
## <a name="value2"></a>Value2  
 **Value2** プロパティは、Excel ブック プロジェクトまたはテンプレート プロジェクトにのみ使用できます。 ワークシート デザイナーで **コントロールを選択すると、[** プロパティ **] ウィンドウの** Databindings <xref:Microsoft.Office.Tools.Excel.NamedRange> プロパティの下に表示されます。  
  
 **の** プロパティをデータ ソースのフィールドにバインドするには、**[プロパティ]** ウィンドウの <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Value2 <xref:Microsoft.Office.Tools.Excel.NamedRange> プロパティを使用します。  
  
## <a name="see-also"></a>関連項目  
 [設計および Office ソリューションを作成します。](../vsto/designing-and-creating-office-solutions.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)  
  
  