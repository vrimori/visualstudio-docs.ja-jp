---
title: InfoPath のリボンをカスタマイズします。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 250e3ed3fb548dad26bc29f83fae35b8e6727c9f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672252"
---
# <a name="customize-a-ribbon-for-infopath"></a>InfoPath のリボンをカスタマイズします。
  Microsoft Office InfoPath でリボンをカスタマイズする場合、アプリケーションのどこにカスタム リボンを表示するかを検討する必要があります。 [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] では、次の 3 種類の InfoPath アプリケーション ウィンドウにリボンを表示できます。  
  
-   デザイン モードで開くフォーム テンプレートを表示するウィンドウ。  
  
-   フォーム テンプレートを基にしたフォームを表示するウィンドウ。  
  
-   [印刷プレビュー] ウィンドウ。  
  
 **対象:** このトピックの情報は、InfoPath 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、次を参照してください。 [Office アプリケーションおよびプロジェクトの種類で使用できる機能](../vsto/features-available-by-office-application-and-project-type.md)します。  
  
 ユーザーとデザイナーは、フォーム テンプレートをデザイン モードで開き、テンプレートの外観とレイアウトを変更します。 ユーザーは、フォーム テンプレートを基にしたフォームを開き、コンテンツを追加します。  
  
 [印刷プレビュー] ウィンドウでは、デザイナーとユーザーがフォームまたはフォーム テンプレートを印刷前にプレビューできます。  
  
> [!NOTE]  
>  [印刷プレビュー] ウィンドウには **[アドイン]** タブは表示されません。 [印刷プレビュー] ウィンドウにカスタム タブを表示する場合は、タブの **OfficeId** プロパティが **TabAddIns**に設定されていないことを確認してください。  
  
 リボンを表示する各ウィンドウのリボンの種類を指定する必要があります。  
  
## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>リボン デザイナーでリボンの種類を指定します。  
 使用する場合、**リボン (ビジュアル デザイナー)** 項目をクリックして、 **[ribbontype]** でリボンのプロパティ、**プロパティ**ウィンドウ、リボン Id のいずれかを選択次の表で説明します。  
  
|リボン ID|プロジェクトの実行時にリボンが表示されるウィンドウ|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|デザイン モードで開くフォーム テンプレートを表示するウィンドウ。|  
|**Microsoft.InfoPath.Editor**|フォーム テンプレートを基にしたフォームを表示するウィンドウ。|  
|**Microsoft.InfoPath.PrintPreview**|[印刷プレビュー] ウィンドウ。|  
  
 1 つのプロジェクトに複数のリボンを追加することができます。 複数のリボンで 1 つのリボン ID を共有する場合は、プロジェクトの `ThisAddin` クラスの `CreateRibbonExtensibilityObject` メソッドをオーバーライドし、実行時に表示するリボンを指定します。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)します。  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>リボン XML を使用して、リボンの種類を指定します。  
 使用する場合、**リボン (XML)** 項目の値を確認してください、 *ribbonID*パラメーター、<xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>メソッドと、適切なリボンを戻り値。  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> メソッドは、Visual Studio によってリボン コード ファイルに自動的に生成されます。 *ribbonID* パラメーターは、開いている InfoPath ウィンドウの種類を識別する文字列です。  
  
 デザイン モードでフォーム テンプレートを表示するウィンドウにのみカスタム リボンを表示する方法を次のコード例に示します。 表示するリボンは、リボン クラスで生成される `GetResourceText()` メソッドで指定します。 リボン クラスの詳細については、「 [Ribbon XML](../vsto/ribbon-xml.md)」を参照してください。  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [実行時にリボンへのアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)  
  
  