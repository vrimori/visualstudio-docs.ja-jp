---
title: 実行時にリボンにアクセスします。
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: abeffdbc61861aae3c0c9c53cb07d597abaa31c9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="access-the-ribbon-at-runtime"></a>実行時にリボンにアクセスします。
  リボンを表示、非表示、変更するコードを作成し、ユーザーがカスタム作業ウィンドウ、アクション ウィンドウ、または Outlook フォーム領域のコントロールからそのコードを実行できるようにすることができます。  

 リボンには、`Globals` クラスを使用してアクセスできます。 Outlook プロジェクトの場合は、特定の Outlook インスペクター ウィンドウまたは Outlook エクスプ ローラー ウィンドウに表示されるリボンにアクセスできます。  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Globals クラスを使用して、リボンにアクセスします。  
 `Globals` クラスを使用して、プロジェクトのどこからでもドキュメント レベルのプロジェクトまたは VSTO アドイン プロジェクトのリボンにアクセスできます。  

 詳細については、`Globals`クラスを参照してください[Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)です。  

 次の例では、`Globals` クラスを使用して `Ribbon1` という名前のカスタム リボンにアクセスし、リボンのコンボ ボックスに表示されるテキストを `Hello World` に設定します。  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>特定の Outlook インスペクター ウィンドウに表示されるリボンのコレクションへのアクセスします。  
 Outlook で表示されるリボンのコレクションにアクセスすることができます*インスペクター*です。 インスペクターは、ユーザーが電子メール メッセージを作成するなど、特定のタスクを実行するときに、Outlook で開かれるウィンドウです。 インスペクター ウィンドウのリボンにアクセスするには、`Globals` クラスの `Ribbons` プロパティを呼び出し、インスペクターを表す <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトを渡します。  

 次の例では、現在フォーカスがあるインスペクターのリボン コレクションを取得します。 この例では次に、`Ribbon1` という名前のリボンにアクセスして、リボンのコンボ ボックスに表示されるテキストを `Hello World` に設定します。  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>特定の Outlook エクスプ ローラーに表示されるリボンのコレクションへのアクセスします。  
 Outlook に表示されるリボンのコレクションにアクセスすることができます*エクスプ ローラー*です。 エクスプ ローラーは、Outlook のインスタンスの主要なアプリケーション ユーザー インターフェイス (UI) です。 エクスプローラー ウィンドウのリボンにアクセスするには、`Globals` クラスの `Ribbons` プロパティを呼び出し、エクスプローラーを表す <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトを渡します。  

 次の例では、現在フォーカスがあるエクスプローラーのリボン コレクションを取得します。 この例では次に、`Ribbon1` という名前のリボンにアクセスして、リボンのコンボ ボックスに表示されるテキストを `Hello World` に設定します。  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: 実行時にリボン上のコントロールを更新します。](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Outlook のリボンをカスタマイズします。](../vsto/customizing-a-ribbon-for-outlook.md)   
 [実行時にフォーム領域にアクセスします。](../vsto/accessing-a-form-region-at-run-time.md)  
