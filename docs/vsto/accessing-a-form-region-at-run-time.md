---
title: 実行時にフォーム領域へのアクセスします。
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at runtime
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 82f613711d1d95b271bd0d1ca558b193a1aa90cb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875434"
---
# <a name="access-a-form-region-at-runtime"></a>実行時にフォーム領域へのアクセスします。

|対象|  
|----------------|  
|このトピックの情報は、次の種類のプロジェクトおよび Microsoft Office のバージョンにのみ適用されます。 詳細については、次を参照してください。 [Office アプリケーションおよびプロジェクトの種類で使用できる機能](../vsto/features-available-by-office-application-and-project-type.md)します。<br /><br /> **プロジェクトの種類**<br /><br /> VSTO アドイン プロジェクト<br /><br /> **Microsoft Office のバージョン**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 `Globals` クラスを使用すると、Outlook プロジェクトの任意の場所からフォーム領域にアクセスできます。 詳細については、`Globals`クラスを参照してください[Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)します。  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>特定の Outlook インスペクター ウィンドウに表示されるフォーム領域をアクセス  
 特定の Outlook インスペクターに表示されるすべてのフォーム領域にアクセスするには、 `FormRegions` クラスの `Globals` プロパティを呼び出し、インスペクターを表す <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトを渡します。  

 次の例では、現在フォーカスが設定されているインスペクターに表示されるフォーム領域のコレクションを取得します。 この例では、次に、 `formRegion1` というコレクション内のフォーム領域にアクセスし、テキスト ボックス内のテキストを `Hello World`に設定します。  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>特定の Outlook エクスプ ローラー ウィンドウに表示されるフォーム領域のアクセス  
 特定の Outlook エクスプローラーに表示されるすべてのフォーム領域にアクセスするには、 `FormRegions` クラスの `Globals` プロパティを呼び出し、エクスプローラーを表す <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトを渡します。  

 次の例では、現在フォーカスが設定されているエクスプローラーに表示されるフォーム領域のコレクションを取得します。 この例では、次に、 `formRegion1` というコレクション内のフォーム領域にアクセスし、テキスト ボックス内のテキストを `Hello World`に設定します。  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="access-all-form-regions"></a>すべてのフォーム領域へのアクセスします。  
 すべてのエクスプローラーおよびすべてのインスペクターに表示されるすべてのフォーム領域にアクセスするには、 `FormRegions` クラスの `Globals` プロパティを呼び出します。  

 次の例では、すべてのエクスプローラーおよびすべてのインスペクターに表示されるフォーム領域のコレクションを取得します。 この例では、次に、 `formRegion1` というフォーム領域にアクセスし、テキスト ボックス内のテキストを `Hello World`に設定します。  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="access-controls-on-a-form-region"></a>フォーム領域のアクセス制御  
 `Globals` クラスを使用してフォーム領域のコントロールにアクセスするには、それらのコントロールを、フォーム領域コード ファイルの外部にあるコードからアクセスできるようにする必要があります。  

### <a name="form-regions-designed-in-the-form-region-designer"></a>フォーム領域をフォーム領域デザイナーでデザイン  
 C# の場合は、アクセス対象にする各コントロールの修飾子を変更します。 この操作を行うには、フォーム領域デザイナーで各コントロールを選択し、 **[プロパティ]** ウィンドウで **Modifiers** プロパティを **Internal** または **public** に変更します。 たとえば、 **の** Modifier `textBox1` プロパティを **Internal**に変更すると、 `textBox1` と入力して `Globals.FormRegions.FormRegion1.textBox1`にアクセスできます。  

 Visual Basic の場合は、修飾子を変更する必要はありません。  

### <a name="imported-form-regions"></a>インポートされたフォーム領域  
 Outlook でデザインされたフォーム領域をインポートすると、フォーム領域上の各コントロールのアクセス修飾子はプライベートになります。 インポートされたフォーム領域をフォーム領域デザイナーで変更することはできないため、 **[プロパティ]** ウィンドウでコントロールの修飾子を変更する方法はありません。  

 フォーム領域コード ファイルの外部からコードにアクセスできるようにするには、フォーム領域コード ファイルに、そのコントロールを返すプロパティを作成します。  

 C# でのプロパティを作成する方法の詳細については、次を参照してください。[方法。宣言し、プロパティの読み取りを使用して書き込み&#40;C&#35;プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties)します。  

 Visual Basic でプロパティを作成する方法の詳細については、次を参照してください。[方法。プロパティ (Visual Basic) を作成する](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property)します。  

## <a name="see-also"></a>関連項目  
 [Outlook フォーム領域を作成するためのガイドライン](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [チュートリアル: Outlook フォーム領域をデザインします。](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [方法: フォーム領域を Outlook アドイン プロジェクトに追加します。](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Outlook フォーム領域のカスタム アクション](../vsto/custom-actions-in-outlook-form-regions.md)   
 [フォーム領域を Outlook メッセージ クラスに関連付ける](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [チュートリアル: Outlook でデザインしたフォーム領域をインポートします。](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [方法: Outlook フォーム領域が表示されないようにします。](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Outlook フォーム領域を作成します。](../vsto/creating-outlook-form-regions.md)   
 [実行時にリボンへのアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)  
