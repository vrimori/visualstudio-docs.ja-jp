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
ms.openlocfilehash: ef1c72d5c24c70a539b909e8d338a235ceb52a49
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="customize-a-ribbon-for-outlook"></a>Outlook のリボンをカスタマイズします。
  Microsoft Office Outlook でリボンをカスタマイズする場合、アプリケーションのどこにカスタム リボンを表示するかを検討する必要があります。 Outlook によりメイン アプリケーション ユーザー インターフェイス (UI) にリボンが表示されます。また、ユーザーが電子メール メッセージの作成など、特定のタスクを実行すると、ウィンドウが開いてリボンが表示されます。 これらのアプリケーション ウィンドウをインスペクターと呼びます。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [How do i: 使用をリボン デザイナーを Outlook でリボンをカスタマイズしますか?](http://go.microsoft.com/fwlink/?LinkID=130312)です。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>カスタム リボン、メイン アプリケーション UI を追加します。  
 Outlook のメインのアプリケーション UI は、エクスプローラーと呼ばれます。 使用している場合、**リボン (ビジュアル デザイナー)**  をクリックしてエクスプ ローラーにリボンを追加する項目を**RibbonType**でリボンのプロパティ、**プロパティ**ウィンドウで、クリックして**microsoft.outlook.explorer**です。  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>インスペクターのリボンを割り当てる  
 インスペクターのメッセージ クラスに対応するリボンの種類を指定することによって、カスタマイズするインスペクターを指定します。  
  
 使用している場合、**リボン (ビジュアル デザイナー)** 項目をクリックして、 **[ribbontype]** でリボンのプロパティ、**プロパティ**ウィンドウ、および選択し、1 つまたは複数のリボンからの Id値のリスト。  
  
 1 つのプロジェクトに複数のリボンを追加することができます。 複数のリボンで 1 つのリボン ID を共有する場合は、プロジェクトの `ThisAddin` クラスの `CreateRibbonExtensibilityObject` メソッドをオーバーライドし、実行時に表示するリボンを指定します。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。 各リボンの種類の詳細については、技術記事を参照してください。 [Outlook 2007 におけるリボンをカスタマイズする](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170)です。  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>リボン XML を使用して、リボンの種類を指定します。  
 使用している場合、**リボン (XML)** 項目の値を確認して、 *ribbonID*内のパラメーター、<xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>メソッドと、適切なリボンを戻り値。  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> メソッドは、Visual Studio によってリボン コード ファイルに自動的に生成されます。 *RibbonID*パラメーターは、エクスプ ローラーまたはインスペクターの特定の種類を識別する文字列。 有効な値の完全な一覧については、 *ribbonID*パラメーター、技術記事を参照してください[Outlook 2007 におけるリボンをカスタマイズする](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170)です。  
  
 次のコード例は、`Microsoft.Outlook.Mail.Compose` インスペクターにのみカスタム リボンを表示する方法を示しています。 これは、ユーザーが新しい電子メール メッセージを作成するときに表示されるインスペクターです。 表示するリボンがで指定された、`GetResourceText()`で生成されるメソッド、**リボン**クラスです。 詳細については、**リボン**クラスを参照してください[リボン XML](../vsto/ribbon-xml.md)です。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [実行時にリボンにアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)  
  
  