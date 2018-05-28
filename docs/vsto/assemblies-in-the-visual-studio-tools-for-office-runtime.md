---
title: Visual Studio Tools for Office ランタイムのアセンブリ
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ff32d472d0e2005b22acb8d751e03c6aa3f61ef
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office ランタイムのアセンブリ
  Office プロジェクトを作成すると、Visual Studio によって、そのプロジェクト タイプとプロジェクトの対象 .NET Framework に使用する [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] アセンブリの参照が自動的に追加されます。 .NET Framework 3.5、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]、 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]の Office 拡張機能にさまざまなアセンブリがあります。 Office 拡張機能の詳細については、次を参照してください。 [Visual Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)です。  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>.NET Framework 4 用の Office 拡張機能内のアセンブリと、 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 次の表は、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] と [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]の Office 拡張機能に含まれているアセンブリをまとめたものです。 名前空間とこれらのアセンブリ内の型に関するドキュメントについては、次を参照してください。[マネージ参照&#40;Visual Studio での Office 開発&#41;](../vsto/managed-reference-office-development-in-visual-studio.md)です。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|次の型を提供します。<br /><br /> リボンのカスタマイズとスマート タグを作成するための型。 **注:** でスマート タグは非推奨[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]と[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]です。<br />ドキュメント レベルのカスタマイズやカスタム作業ウィンドウでは、VSTO アドインで操作ウィンドウを作成するための型。|  
|Microsoft.Office.Tools.Excel.dll|Excel プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、次を参照してください。[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)です。|  
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できる型を提供します。|  
|Microsoft.Office.Tools.Word.dll|Word プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、次を参照してください。[拡張オブジェクトを使用して Word を自動化](../vsto/automating-word-by-using-extended-objects.md)です。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|次の型を提供します。<br /><br /> -Visual Studio Tools for Office ランタイムによってスローされる例外。<br />フォーム領域の属性の Outlook を作成するときに使用することができます。|  
|Microsoft.Office.Tools.dll|Visual Studio Tools for Office Runtime インフラストラクチャに属し、コードから直接使用するものではない型を提供します。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性と<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>インターフェイスで、ドキュメント レベルのカスタマイズでキャッシュ データ オブジェクトに使用することができます。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)です。<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できるインターフェイス。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)です。<br />-Visual Studio Tools for Office ランタイムによってスローされる例外。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスで、カスタマイズ アセンブリをドキュメントにアタッチし、ドキュメントでキャッシュされたデータにアクセスを行うこともできます。 詳細については、次を参照してください。 [ServerDocument クラスを使用して、サーバー上のドキュメントを管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)です。<br />、階層を表すいくつかのクラスには、ドキュメント レベルのカスタマイズ内のデータがキャッシュされます。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)です。|  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトは次のアセンブリも参照します。 これらのアセンブリは再頒布可能な [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] に含まれません。 これらはむしろ、ソリューションで展開しなければならない従属アセンブリです。 既定では、プロジェクトのビルド出力フォルダーにコピーされます (これらのアセンブリの **[ローカル コピー]** プロパティは **True**に設定されます)。 ClickOnce を使用してプロジェクトを展開する場合、これらのアセンブリは生成されたパッケージに含まれます。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|VSTO アドイン プロジェクトで生成される `ThisAddIn` クラスとすべてのプロジェクトで生成される Ribbon クラスの基底クラスを提供します。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -基本、生成されたクラス`ThisWorkbook`と`Sheet`内のクラスのドキュメント レベル プロジェクト Excel 用です。<br />Excel プロジェクトのワークシートで使用できる Windows フォーム コントロール。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Outlook プロジェクトで生成される `ThisAddIn` とフォーム領域クラスの基本クラスを提供します。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -基本、生成されたクラス`ThisDocument`Word 用ドキュメント レベルのプロジェクト内のクラスです。<br />Word プロジェクトのドキュメントで使用できる Windows フォーム コントロール。|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3.5 用の Office 拡張機能内のアセンブリ  
 次の表は、.NET Framework 3.5 の Office 拡張機能に含まれているアセンブリをまとめたものです。 名前空間とこれらのアセンブリ内のクラスに関するドキュメントについては、Visual Studio 2008 ドキュメントの次の参照セクションを参照してください: [ http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)です。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|次の型を提供します。<br /><br /> -Microsoft.Office.Tools.AddIn 基底クラスには、VSTO アドイン。<br />リボンのカスタマイズとスマート タグを作成するためのクラス。 **注:** でスマート タグは非推奨[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]と[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]です。<br />ドキュメント レベルのカスタマイズやカスタム作業ウィンドウでは、VSTO アドインで操作ウィンドウを作成するためのクラス。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Excel ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、次を参照してください。[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)です。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できるクラスを提供します。|  
|Microsoft.Office.Tools.Word.v9.0.dll|Word ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、次を参照してください。[拡張オブジェクトを使用して Word を自動化](../vsto/automating-word-by-using-extended-objects.md)です。|  
|Microsoft.Office.Tools.v9.0.dll|次の型を提供します。<br /><br /> - [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90))でホスト コントロールのドキュメント レベルのカスタマイズのデータ バインディング機能を提供するクラス。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性と<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>インターフェイスで、ドキュメント レベルのカスタマイズでキャッシュ データ オブジェクトに使用することができます。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)です。<br />-Visual Studio Tools for Office ランタイムによってスローされる例外。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できる <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> インターフェイスを提供します。 詳細については、次を参照してください。[高度な Office ソリューションの配置](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02)です。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスは、プログラムでカスタマイズ アセンブリをドキュメントにアタッチして、ドキュメントでキャッシュされたデータにアクセスを行うこともできます。 詳細については、次を参照してください。 [ServerDocument クラスを使用して、サーバー上のドキュメントを管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)です。<br />、階層を表すいくつかのクラスには、ドキュメント レベルのカスタマイズ内のデータがキャッシュされます。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)です。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|次の型を提供します。<br /><br /> リストのエントリを Office に信頼を与えるユーザー信頼の作成に使用できる-Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry および Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList クラス.NET Framework 3.5 を対象とするソリューションです。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の型。|  
  
## <a name="see-also"></a>関連項目  
 [ビジュアルの Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [ビジュアルの Studio Tools for Office runtime のインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  