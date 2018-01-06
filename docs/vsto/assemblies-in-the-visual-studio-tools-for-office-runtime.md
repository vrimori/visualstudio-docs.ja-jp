---
title: "Visual Studio Tools for Office Runtime のアセンブリ |Microsoft ドキュメント"
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
helpviewer_keywords: Visual Studio Tools for Office runtime, assemblies
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dff032c3f43c662b75f4d0b757f16e70095efc33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime のアセンブリ
  Office プロジェクトを作成すると、Visual Studio によって、そのプロジェクト タイプとプロジェクトの対象 .NET Framework に使用する [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] アセンブリの参照が自動的に追加されます。 .NET Framework 3.5、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]、 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]の Office 拡張機能にさまざまなアセンブリがあります。 Office 拡張機能についての詳細は、「 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>.NET Framework 4 と [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]の Office 拡張機能に含まれるアセンブリ  
 次の表は、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] と [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]の Office 拡張機能に含まれているアセンブリをまとめたものです。 名前空間とこれらのアセンブリ内の型に関するドキュメントについては、次を参照してください。[マネージ参照 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/managed-reference-office-development-in-visual-studio.md)です。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|次の型を提供します。<br /><br /> リボンのカスタマイズとスマート タグを作成するための型。 **注:**でスマート タグは非推奨[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]と[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]です。<br />ドキュメント レベルのカスタマイズやカスタム作業ウィンドウでは、VSTO アドインで操作ウィンドウを作成するための型。|  
|Microsoft.Office.Tools.Excel.dll|Excel プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、「 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できる型を提供します。|  
|Microsoft.Office.Tools.Word.dll|Word プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、「 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|次の型を提供します。<br /><br /> -Visual Studio Tools for Office ランタイムによってスローされる例外。<br />フォーム領域の属性の Outlook を作成するときに使用することができます。|  
|Microsoft.Office.Tools.dll|Visual Studio Tools for Office Runtime インフラストラクチャに属し、コードから直接使用するものではない型を提供します。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性と<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>インターフェイスで、ドキュメント レベルのカスタマイズでキャッシュ データ オブジェクトに使用することができます。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できるインターフェイス。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)です。<br />-Visual Studio Tools for Office ランタイムによってスローされる例外。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスで、カスタマイズ アセンブリをドキュメントにアタッチし、ドキュメントでキャッシュされたデータにアクセスを行うこともできます。 詳細については、「 [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)」を参照してください。<br />、階層を表すいくつかのクラスには、ドキュメント レベルのカスタマイズ内のデータがキャッシュされます。 詳細については、「 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。|  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトは次のアセンブリも参照します。 これらのアセンブリは再頒布可能な [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] に含まれません。 これらはむしろ、ソリューションで展開しなければならない従属アセンブリです。 既定では、プロジェクトのビルド出力フォルダーにコピーされます (これらのアセンブリの **[ローカル コピー]** プロパティは **True**に設定されます)。 ClickOnce を使用してプロジェクトを展開する場合、これらのアセンブリは生成されたパッケージに含まれます。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|VSTO アドイン プロジェクトで生成される `ThisAddIn` クラスとすべてのプロジェクトで生成される Ribbon クラスの基底クラスを提供します。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -基本、生成されたクラス`ThisWorkbook`と`Sheet`内のクラスのドキュメント レベル プロジェクト Excel 用です。<br />Excel プロジェクトのワークシートで使用できる Windows フォーム コントロール。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Outlook プロジェクトで生成される `ThisAddIn` とフォーム領域クラスの基本クラスを提供します。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -基本、生成されたクラス`ThisDocument`Word 用ドキュメント レベルのプロジェクト内のクラスです。<br />Word プロジェクトのドキュメントで使用できる Windows フォーム コントロール。|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3.5 の Office 拡張機能のアセンブリ  
 次の表は、.NET Framework 3.5 の Office 拡張機能に含まれているアセンブリをまとめたものです。 これらのアセンブリの名前空間とクラスの詳細については、Visual Studio 2008 ドキュメントの参照セクション [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)を参照してください。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|次の型を提供します。<br /><br /> -Microsoft.Office.Tools.AddIn 基底クラスには、VSTO アドイン。<br />リボンのカスタマイズとスマート タグを作成するためのクラス。 **注:**でスマート タグは非推奨[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]と[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]です。<br />ドキュメント レベルのカスタマイズやカスタム作業ウィンドウでは、VSTO アドインで操作ウィンドウを作成するためのクラス。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Excel ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、「 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できるクラスを提供します。|  
|Microsoft.Office.Tools.Word.v9.0.dll|Word ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、「 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)」を参照してください。|  
|Microsoft.Office.Tools.v9.0.dll|次の型を提供します。<br /><br /> -Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent クラス ドキュメント レベルのカスタマイズでホスト コントロールのデータ バインディング機能を提供します。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|次の型を提供します。<br /><br /> -Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute 属性と Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType インターフェイスは、ドキュメント レベルのカスタマイズでキャッシュ データ オブジェクトに使用することができます。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。<br />-Visual Studio Tools for Office ランタイムによってスローされる例外。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できる Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction インターフェイスを提供します。 詳細については、「 [Advanced Office Solution Deployment](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02)」を参照してください。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|次の型を提供します。<br /><br /> -Microsoft.VisualStudio.Tools.Applications.ServerDocument クラスをプログラムでカスタマイズ アセンブリをドキュメントにアタッチして、ドキュメントでキャッシュされたデータにアクセスを行うこともできます。 詳細については、「 [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)」を参照してください。<br />、階層を表すいくつかのクラスには、ドキュメント レベルのカスタマイズ内のデータがキャッシュされます。 詳細については、「 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|次の型を提供します。<br /><br /> リストのエントリを Office に信頼を与えるユーザー信頼の作成に使用できる-Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry および Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList クラス.NET Framework 3.5 を対象とするソリューションです。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
  
## <a name="see-also"></a>参照  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office ランタイムのインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  