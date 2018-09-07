---
title: Outlook のリボンをカスタマイズします。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 572b92d6a74a3ef61f85e13494856c1193a7770f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673099"
---
# <a name="customize-a-ribbon-for-outlook"></a>Outlook のリボンをカスタマイズします。
  Microsoft Office Outlook でリボンをカスタマイズする場合、アプリケーションのどこにカスタム リボンを表示するかを検討する必要があります。 Outlook によりメイン アプリケーション ユーザー インターフェイス (UI) にリボンが表示されます。また、ユーザーが電子メール メッセージの作成など、特定のタスクを実行すると、ウィンドウが開いてリボンが表示されます。 これらのアプリケーション ウィンドウをインスペクターと呼びます。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [How do i: 使用をリボン デザイナーを Outlook でリボンをカスタマイズしますか?](http://go.microsoft.com/fwlink/?LinkID=130312)します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>カスタム リボン、メイン アプリケーション UI を追加します。  
 Outlook のメインのアプリケーション UI は、エクスプローラーと呼ばれます。 使用する場合、**リボン (ビジュアル デザイナー)** クリックして、エクスプ ローラーにリボンを追加する項目を**ribbontype**でリボンのプロパティ、**プロパティ**ウィンドウで、選択**Microsoft.Outlook.Explorer**します。  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>インスペクターのリボンを割り当てる  
 インスペクターのメッセージ クラスに対応するリボンの種類を指定することによって、カスタマイズするインスペクターを指定します。  
  
 使用する場合、**リボン (ビジュアル デザイナー)** 項目をクリックして、 **ribbontype**でリボンのプロパティ、**プロパティ**ウィンドウと 1 つ以上のリボンからの Id値のリスト。  
  
 1 つのプロジェクトに複数のリボンを追加することができます。 複数のリボンで 1 つのリボン ID を共有する場合は、プロジェクトの `ThisAddin` クラスの `CreateRibbonExtensibilityObject` メソッドをオーバーライドし、実行時に表示するリボンを指定します。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)します。 リボンの各種類に関する詳細については、技術記事を参照してください。 [Outlook 2007 でリボンをカスタマイズ](http://msdn.microsoft.com/946e97ea-f556-4e84-8fac-01cd9214e170)します。  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>リボン XML を使用して、リボンの種類を指定します。  
 使用する場合、**リボン (XML)** 項目の値を確認してください、 *ribbonID*パラメーター、<xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>メソッドと、適切なリボンを戻り値。  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> メソッドは、Visual Studio によってリボン コード ファイルに自動的に生成されます。 *RibbonID*パラメーターは、エクスプ ローラーまたはインスペクターの特定の種類を識別する文字列。 可能な値の完全な一覧については、 *ribbonID*パラメーター、技術記事を参照してください。 [Outlook 2007 でリボンをカスタマイズ](http://msdn.microsoft.com/946e97ea-f556-4e84-8fac-01cd9214e170)します。  
  
 次のコード例は、`Microsoft.Outlook.Mail.Compose` インスペクターにのみカスタム リボンを表示する方法を示しています。 これは、ユーザーが新しい電子メール メッセージを作成するときに表示されるインスペクターです。 表示するリボンがで指定された、`GetResourceText()`メソッドで生成される、**リボン**クラス。 詳細については、**リボン**クラスを参照してください[リボン XML](../vsto/ribbon-xml.md)します。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [実行時にリボンへのアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)  
  
  