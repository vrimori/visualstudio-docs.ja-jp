---
title: Office ソリューションの遅延バインディング
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 5616ce958747f90c8015df858f657299ba52852b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572551"
---
# <a name="late-binding-in-office-solutions"></a>Office ソリューションの遅延バインディング
  Office アプリケーションのオブジェクト モデルの種類によっては、遅延バインディング機能を介して使用可能な機能を提供します。 たとえば、一部のメソッドとプロパティは、異なる種類の Office アプリケーションのコンテキストによってオブジェクトを返すことができ、一部の型は、さまざまな方法または別のコンテキストでのプロパティを公開できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic プロジェクト where **Option Strict** off および Visual c# プロジェクトをターゲットとするには、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]これら遅延バインディングの機能を利用している型を直接操作できます。  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>オブジェクトの明示的および暗黙的なキャストが値を返す  
 多くのメソッドとプロパティには、Microsoft Office プライマリ相互運用機能アセンブリ (Pia) を返す<xref:System.Object>値は、いくつかの異なる種類のオブジェクトを返せるためです。 たとえば、<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A>プロパティから返される、<xref:System.Object>その戻り値ができるので、<xref:Microsoft.Office.Interop.Excel.Worksheet>または<xref:Microsoft.Office.Interop.Excel.Chart>によっては、アクティブなシート オブジェクトです。  
  
 メソッドまたはプロパティが返されるときに、 <xref:System.Object>、する必要があります明示的に変換する (Visual Basic) のオブジェクトを Visual Basic プロジェクトで正しい型場所**Option Strict**にします。 明示的にキャストする必要はありません<xref:System.Object>Visual Basic プロジェクトで値を返す場所**Option Strict**がオフです。  
  
 ほとんどの場合、参照ドキュメントを返すメンバーの戻り値の種類を一覧表示、<xref:System.Object>です。 オブジェクトをキャストまたは変換オブジェクト コード エディターでの IntelliSense を有効にします。  
  
 Visual Basic での変換については、次を参照してください。[暗黙的および明示的な変換&#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)と[CType 関数&#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function)です。  
  
### <a name="examples"></a>使用例  
 次のコード例を Visual Basic プロジェクトでオブジェクトを特定の型にキャストする方法を示しています、 **Option Strict**にします。 このプロジェクトの種類である必要があります明示的にキャストする、<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>プロパティを<xref:Microsoft.Office.Interop.Excel.Range>です。 この例では、という名前のワークシート クラスとドキュメント レベルの Excel プロジェクトが必要があります`Sheet1`です。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 次のコード例を Visual Basic プロジェクトでオブジェクトを特定の型に暗黙的にキャストする方法を示しています、 **Option Strict**入っていないか、Visual c# プロジェクトを対象とする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]です。 これらの種類のプロジェクトで、<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>プロパティに暗黙的にキャスト、<xref:Microsoft.Office.Interop.Excel.Range>です。 この例では、という名前のワークシート クラスとドキュメント レベルの Excel プロジェクトが必要があります`Sheet1`です。  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>遅延バインディングでのみ利用可能なメンバーにアクセス  
 一部のプロパティと、Office Pia のメソッドは、遅延バインディングを介してのみ使用します。 Visual Basic のプロジェクトの場所**Option Strict**がオフまたは Visual c# プロジェクトをターゲットとする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]、遅延バインディング メンバーにアクセスするこれらの言語で遅延バインディング機能を使用することができます。 Visual basic プロジェクト where **Option Strict**は、リフレクションを使用してこれらのメンバーにアクセスする必要があります。  
  
### <a name="examples"></a>使用例  
 次のコード例を Visual Basic プロジェクトで遅延バインディング メンバーにアクセスする方法を示しています、 **Option Strict**入っていないか、Visual c# プロジェクトを対象とする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]です。 この例は、遅延バインディング**名前**のプロパティ、**ファイルを開く**Word のダイアログ ボックス。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`Word プロジェクトのクラスです。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 次のコード例では、リフレクションを使用して、Visual Basic プロジェクトで同じタスクを実行する場所**Option Strict**にします。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Dynamic 型の使用&#40;C&#35;プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict ステートメント](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [リフレクション (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [リフレクション (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [設計および Office ソリューションを作成します。](../vsto/designing-and-creating-office-solutions.md)  
  
  