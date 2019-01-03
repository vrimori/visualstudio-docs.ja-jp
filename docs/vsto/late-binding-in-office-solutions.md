---
title: Office ソリューションの遅延バインディング
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c886305b3cfe63ef2d2821752d97099d93689891
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847257"
---
# <a name="late-binding-in-office-solutions"></a>Office ソリューションの遅延バインディング
  Office アプリケーションのオブジェクト モデルの一部の型は、遅延バインディングの機能で使用可能な機能を提供します。 たとえば、いくつかのメソッドとプロパティは、さまざまな種類の Office アプリケーションのコンテキストに応じてオブジェクトを返すことができ、一部の種類は、さまざまな方法または別のコンテキストでのプロパティを公開できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic プロジェクト where **Option Strict**オフし、Visual c# プロジェクトを対象とするには、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]これらの遅延バインディング機能を利用している型を直接操作できます。  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>戻り値のオブジェクトの明示的および暗黙的なキャスト  
 多くのメソッドとプロパティには、Microsoft Office プライマリ相互運用機能アセンブリ (Pia) を返す<xref:System.Object>値は、いくつかの異なる種類のオブジェクトを返せるためです。 など、<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A>プロパティが返す、<xref:System.Object>その戻り値ができるので、<xref:Microsoft.Office.Interop.Excel.Worksheet>または<xref:Microsoft.Office.Interop.Excel.Chart>によってアクティブなシートは、オブジェクト。  
  
 メソッドまたはプロパティが返されるときに、 <xref:System.Object>、する必要があります明示的にオブジェクトを変換する (Visual Basic) で Visual Basic プロジェクトで正しい型に、 **Option Strict**にします。 明示的にキャストする必要はありません<xref:System.Object>Visual Basic プロジェクトで値を返す場所**Option Strict**はオフです。  
  
 ほとんどの場合、リファレンス ドキュメントを返すメンバーの戻り値の種類を一覧表示、<xref:System.Object>します。 オブジェクトをキャストまたは変換は、オブジェクト コード エディターで IntelliSense を使用できます。  
  
 Visual Basic での変換については、次を参照してください。[暗黙的および明示的な変換&#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)と[CType function &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function)します。  
  
### <a name="examples"></a>使用例  
 次のコード例は、Visual Basic プロジェクトでオブジェクトを特定の型をキャストする方法を示します、 **Option Strict**にします。 この種類のプロジェクトでは、キャストする必要が明示的に、<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>プロパティを<xref:Microsoft.Office.Interop.Excel.Range>します。 この例では、という名前のワークシート クラスを使用して Excel のドキュメント レベルのプロジェクトが必要があります`Sheet1`します。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 次のコード例は、Visual Basic プロジェクトでオブジェクトを特定の型を暗黙的にキャストする方法を示します、 **Option Strict**を対象とする Visual c# プロジェクトでは、オフ、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]します。 これらの種類のプロジェクトで、<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>プロパティに暗黙的にキャスト、<xref:Microsoft.Office.Interop.Excel.Range>します。 この例では、という名前のワークシート クラスを使用して Excel のドキュメント レベルのプロジェクトが必要があります`Sheet1`します。  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>遅延バインディングでのみ利用可能なメンバーへのアクセス  
 いくつかのプロパティおよびメソッドに Office Pia は、遅延バインディングを介してのみ使用します。 Visual Basic でプロジェクトを where **Option Strict**がオフまたは Visual c# プロジェクトを対象とする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]、遅延バインディング メンバーにアクセスするこれらの言語で遅延バインド機能を使用することができます。 Visual basic プロジェクト where **Option Strict**に、リフレクションを使用して、これらのメンバーにアクセスする必要があります。  
  
### <a name="examples"></a>使用例  
 次のコード例は、Visual Basic プロジェクトで遅延バインディング メンバーにアクセスする方法を示します、 **Option Strict**を対象とする Visual c# プロジェクトでは、オフ、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]します。 この例は、遅延バインディング**名前**のプロパティ、**ファイルを開く**Word のダイアログ ボックス。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`Word プロジェクトでクラス。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 次のコード例は、リフレクションを使用して、Visual Basic プロジェクトで同じタスクを実行する方法を示します、 **Option Strict**にします。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Dynamic 型の使用&#40;C&#35;プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict ステートメント](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [リフレクション (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [リフレクション (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)  
