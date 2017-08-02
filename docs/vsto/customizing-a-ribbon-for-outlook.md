---
title: "Outlook のリボンのカスタマイズ"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "カスタム リボン, リボンのカスタマイズの概要"
  - "カスタマイズ (リボンを), リボンのカスタマイズの概要"
  - "インスペクター [Visual Studio での Office 開発]"
  - "Outlook [Visual Studio での Office 開発], リボン"
  - "リボン [Visual Studio での Office 開発], Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Outlook のリボンのカスタマイズ
  Microsoft Office Outlook でリボンをカスタマイズする場合、アプリケーションのどこにカスタム リボンを表示するかを検討する必要があります。  Outlook によりメイン アプリケーション ユーザー インターフェイス \(UI\) にリボンが表示されます。また、ユーザーが電子メール メッセージの作成など、特定のタスクを実行すると、ウィンドウが開いてリボンが表示されます。  これらのアプリケーション ウィンドウをインスペクターと呼びます。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[操作方法: リボン デザイナーを使用して Outlook のリボンをカスタマイズする](http://go.microsoft.com/fwlink/?LinkID=130312)」を参照してください。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## メイン アプリケーション UI へのカスタム リボンの追加  
 Outlook のメインのアプリケーション UI は、エクスプローラーと呼ばれます。  **リボン \(ビジュアル デザイナー\)** 項目を使用する場合は、**\[プロパティ\]** ウィンドウでリボンの **\[RibbonType\]** プロパティをクリックしてから、**\[Microsoft.Outlook.Explorer\]** を選択すると、エクスプローラーにリボンを追加できます。  
  
## インスペクターへのリボンの割り当て  
 インスペクターのメッセージ クラスに対応するリボンの種類を指定することによって、カスタマイズするインスペクターを指定します。  
  
 **リボン \(ビジュアル デザイナー\)** 項目を使用する場合は、**\[プロパティ\]** ウィンドウでリボンの **\[RibbonType\]** プロパティをクリックし、値の一覧から 1 つ以上のリボン ID を選択します。  
  
 1 つのプロジェクトに複数のリボンを追加することができます。  複数のリボンで 1 つのリボン ID を共有する場合は、プロジェクトの `ThisAddin` クラスの CreateRibbonExtensibilityObject メソッドをオーバーライドし、実行時に表示するリボンを指定します。  詳細については、「[リボンの概要](../vsto/ribbon-overview.md)」を参照してください。  リボンのそれぞれの種類の詳細については、技術記事「[Outlook 2007 におけるリボンのカスタマイズ](http://msdn.microsoft.com/ja-jp/946e97ea-f556-4e84-8fac-01cd9214e170)」を参照してください。  
  
## リボン XML を使用したリボンの種類の指定  
 **リボン \(XML\)** 項目を使用する場合は、<xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> メソッドの *ribbonID* パラメーターの値を調べて、適切なリボンを返します。  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> メソッドは、Visual Studio によってリボン コード ファイルに自動的に生成されます。  *ribbonID* パラメーターは、エクスプローラーまたは特定の種類のインスペクターを識別する文字列です。  *ribbonID* パラメーターに有効な値の完全な一覧については、技術記事「[Outlook 2007 におけるリボンのカスタマイズ](http://msdn.microsoft.com/ja-jp/946e97ea-f556-4e84-8fac-01cd9214e170)」を参照してください。  
  
 次のコード例は、`Microsoft.Outlook.Mail.Compose` インスペクターにのみカスタム リボンを表示する方法を示しています。  これは、ユーザーが新しい電子メール メッセージを作成するときに表示されるインスペクターです。  表示するリボンは、**Ribbon** クラスに生成される `GetResourceText()` メソッドで指定します。  **Ribbon** クラスの詳細については、「[リボン XML](../vsto/ribbon-xml.md)」を参照してください。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## 参照  
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)  
  
  