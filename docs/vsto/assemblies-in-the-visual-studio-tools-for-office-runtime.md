---
title: "Visual Studio Tools for Office Runtime のアセンブリ | Microsoft Docs"
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
  - "Visual Studio Tools for Office runtime、アセンブリ"
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Visual Studio Tools for Office Runtime のアセンブリ
  Office プロジェクトを作成すると、Visual Studio によって、そのプロジェクト タイプとプロジェクトの対象 .NET Framework に使用する [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] アセンブリの参照が自動的に追加されます。 .NET Framework 3.5、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]、[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] の Office 拡張機能にさまざまなアセンブリがあります。 Office 拡張機能についての詳細は、「[Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
## .NET Framework 4 と [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] の Office 拡張機能に含まれるアセンブリ  
 次の表は、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] と [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] の Office 拡張機能に含まれているアセンブリをまとめたものです。 これらのアセンブリの名前空間と型の詳細については、「[マネージ参照 &#40;Visual Studio での Office 開発&#41;](../vsto/managed-reference-office-development-in-visual-studio.md)」を参照してください。  
  
|\[アセンブリ名\]|説明|  
|----------------|--------|  
|Microsoft.Office.Tools.Common.dll|次の型を提供します。<br /><br /> -   リボンのカスタマイズとスマート タグを作成するための型。 **Note:**      スマート タグは、[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] では使用されていません。<br />-   ドキュメント レベルのカスタマイズの操作ウィンドウと VSTO アドインのカスタム作業ウィンドウを作成するための型。|  
|Microsoft.Office.Tools.Excel.dll|Excel プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、「[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できる型を提供します。|  
|Microsoft.Office.Tools.Word.dll|Word プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、「[拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|次の型を提供します。<br /><br /> -   Visual Studio Tools for Office Runtime によってスローされる例外。<br />-   Outlook フォーム領域の作成時に使用できる属性。|  
|Microsoft.Office.Tools.dll|Visual Studio Tools for Office Runtime インフラストラクチャに属し、コードから直接使用するものではない型を提供します。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|次の型を提供します。<br /><br /> -   ドキュメントレベル カスタマイズでデータ オブジェクトのキャッシュに使用できる <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性と <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> インターフェイス。 詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。<br />-   Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できる <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> インターフェイス。 詳細については、「[ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)」を参照してください。<br />-   Visual Studio Tools for Office Runtime によってスローされる例外。<br />-   Visual Studio Tools for Office Runtime インフラストラクチャに属するその他の種類。これらは、コードから直接使用するものではありません。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|次の型を提供します。<br /><br /> -   カスタマイズ アセンブリをドキュメントに添付し、ドキュメントでキャッシュされたデータにアクセスするために使用できる <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラス。 詳細については、「[ServerDocument クラスによるサーバー上のドキュメントの管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)」を参照してください。<br />-   ドキュメントレベル カスタマイズでキャッシュされたデータの階層を表すいくつかのクラス。 詳細については、「[サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。|  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトは次のアセンブリも参照します。 これらのアセンブリは再頒布可能な [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] に含まれません。 これらはむしろ、ソリューションで展開しなければならない従属アセンブリです。 既定では、プロジェクトのビルド出力フォルダーにコピーされます \(これらのアセンブリの **\[ローカル コピー\]** プロパティは **True** に設定されます\)。 ClickOnce を使用してプロジェクトを展開する場合、これらのアセンブリは生成されたパッケージに含まれます。  
  
|\[アセンブリ名\]|説明|  
|----------------|--------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|VSTO アドイン プロジェクトで生成される `ThisAddIn` クラスとすべてのプロジェクトで生成される Ribbon クラスの基底クラスを提供します。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -   Excel のドキュメントレベル プロジェクトで生成される `ThisWorkbook` クラスと `Sheet` クラスの基本クラス。<br />-   Excel プロジェクトのワークシートで使用できる Windows フォーム コントロール。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Outlook プロジェクトで生成される `ThisAddIn` とフォーム領域クラスの基本クラスを提供します。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -   Word のドキュメントレベル プロジェクトで生成される `ThisDocument` クラスの基本クラス。<br />-   Word プロジェクトの文書で使用できる Windows フォーム コントロール。|  
  
## .NET Framework 3.5 の Office 拡張機能のアセンブリ  
 次の表は、.NET Framework 3.5 の Office 拡張機能に含まれているアセンブリをまとめたものです。 これらのアセンブリの名前空間とクラスの詳細については、Visual Studio 2008 ドキュメントの参照セクション [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658) を参照してください。  
  
|\[アセンブリ名\]|説明|  
|----------------|--------|  
|Microsoft.Office.Tools.Common.v9.0.dll|次の型を提供します。<br /><br /> -   VSTO アドインの Microsoft.Office.Tools.AddIn 基底クラス。<br />-   リボンのカスタマイズとスマート タグを作成するためのクラス。 **Note:**      スマート タグは、[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] では使用されていません。<br />-   ドキュメント レベルのカスタマイズの操作ウィンドウと VSTO アドインのカスタム作業ウィンドウを作成するためのクラス。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Excel ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、「[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できるクラスを提供します。|  
|Microsoft.Office.Tools.Word.v9.0.dll|Word ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、「[拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.v9.0.dll|次の型を提供します。<br /><br /> -   ドキュメントレベル カスタマイズでホスト コントロールのデータ バインディング機能を提供する Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent クラス。<br />-   Visual Studio Tools for Office Runtime インフラストラクチャに属するその他の種類。これらは、コードから直接使用するものではありません。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|次の型を提供します。<br /><br /> -   ドキュメントレベル カスタマイズでデータ オブジェクトのキャッシュに使用できる Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute 属性と Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType インターフェイス。 詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。<br />-   Visual Studio Tools for Office Runtime によってスローされる例外。<br />-   Visual Studio Tools for Office Runtime インフラストラクチャに属するその他の種類。これらは、コードから直接使用するものではありません。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できる Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction インターフェイスを提供します。 詳細については、「[高度な Office ソリューション展開](http://msdn.microsoft.com/ja-jp/9147b6f6-849f-4cb1-b2c5-e22658d74b02)」を参照してください。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|次の型を提供します。<br /><br /> -   プログラミングでカスタマイズ アセンブリをドキュメントに添付し、ドキュメントでキャッシュされたデータにアクセスするために使用できる Microsoft.VisualStudio.Tools.Applications.ServerDocument クラス。 詳細については、「[ServerDocument クラスによるサーバー上のドキュメントの管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)」を参照してください。<br />-   ドキュメントレベル カスタマイズでキャッシュされたデータの階層を表すいくつかのクラス。 詳細については、「[サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|次の型を提供します。<br /><br /> -   .NET Framework 3.5 を対象とする Office ソリューションに信頼を与えるユーザー信頼リスト エントリの作成に使用できる Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry クラスと Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList クラス。<br />-   Visual Studio Tools for Office Runtime インフラストラクチャに属するその他の種類。これらは、コードから直接使用するものではありません。|  
  
## 参照  
 [Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office ランタイムのインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  