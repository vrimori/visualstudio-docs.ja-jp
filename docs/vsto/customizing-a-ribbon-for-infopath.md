---
title: "InfoPath のリボンをカスタマイズ |Microsoft ドキュメント"
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
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
ms.assetid: 498c6457-679a-46f2-939f-c0597a17b7ec
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3f4612b3e8dc272b0f51bae80d66d8afe97938e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-a-ribbon-for-infopath"></a>InfoPath のリボンのカスタマイズ
  Microsoft Office InfoPath でリボンをカスタマイズする場合、アプリケーションのどこにカスタム リボンを表示するかを検討する必要があります。 [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] では、次の 3 種類の InfoPath アプリケーション ウィンドウにリボンを表示できます。  
  
-   デザイン モードで開くフォーム テンプレートを表示するウィンドウ。  
  
-   フォーム テンプレートを基にしたフォームを表示するウィンドウ。  
  
-   [印刷プレビュー] ウィンドウ。  
  
 **対象:** このトピックの情報は、InfoPath 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、「 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
 ユーザーとデザイナーは、フォーム テンプレートをデザイン モードで開き、テンプレートの外観とレイアウトを変更します。 ユーザーは、フォーム テンプレートを基にしたフォームを開き、コンテンツを追加します。  
  
 [印刷プレビュー] ウィンドウでは、デザイナーとユーザーがフォームまたはフォーム テンプレートを印刷前にプレビューできます。  
  
> [!NOTE]  
>  [印刷プレビュー] ウィンドウには **[アドイン]** タブは表示されません。 [印刷プレビュー] ウィンドウにカスタム タブを表示する場合は、タブの **OfficeId** プロパティが **TabAddIns**に設定されていないことを確認してください。  
  
 リボンを表示する各ウィンドウのリボンの種類を指定する必要があります。  
  
## <a name="specifying-the-ribbon-type-in-the-ribbon-designer"></a>リボン デザイナーでのリボンの種類の指定  
 **リボン (ビジュアルなデザイナー)** 項目を使用する場合は、 **[プロパティ]** ウィンドウでリボンの **[RibbonType]** プロパティをクリックし、次の表に示すリボン ID を選択します。  
  
|リボン ID|プロジェクトの実行時にリボンが表示されるウィンドウ|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|デザイン モードで開くフォーム テンプレートを表示するウィンドウ。|  
|**Microsoft.InfoPath.Editor**|フォーム テンプレートを基にしたフォームを表示するウィンドウ。|  
|**Microsoft.InfoPath.PrintPreview**|[印刷プレビュー] ウィンドウ。|  
  
 1 つのプロジェクトに複数のリボンを追加することができます。 1 つ以上のリボンは、リボン ID を共有している場合で CreateRibbonExtensibilityObject メソッドをオーバーライド、`ThisAddin`実行時に表示するリボンを指定するようにプロジェクトのクラスです。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>リボン XML を使用したリボンの種類の指定  
 使用している場合、**リボン (XML)**項目の値を確認して、 *ribbonID*内のパラメーター、<xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>メソッドと、適切なリボンを戻り値。  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> メソッドは、Visual Studio によってリボン コード ファイルに自動的に生成されます。 *ribbonID* パラメーターは、開いている InfoPath ウィンドウの種類を識別する文字列です。  
  
 デザイン モードでフォーム テンプレートを表示するウィンドウにのみカスタム リボンを表示する方法を次のコード例に示します。 表示するリボンは、リボン クラスで生成される `GetResourceText()` メソッドで指定します。 リボン クラスの詳細については、「 [Ribbon XML](../vsto/ribbon-xml.md)」を参照してください。  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)  
  
  