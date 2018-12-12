---
title: Visual Studio Tools for Office ランタイムのアセンブリ
titleSuffix: ''
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66ee95d4f102ac4206a9ed55a1fc97fc251c4f9c
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248117"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office ランタイムのアセンブリ
  Office プロジェクトを作成すると、Visual Studio によって、そのプロジェクト タイプとプロジェクトの対象 .NET Framework に使用する [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] アセンブリの参照が自動的に追加されます。 .NET Framework 3.5、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]、 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]の Office 拡張機能にさまざまなアセンブリがあります。 Office 拡張機能の詳細については、次を参照してください。 [Visual Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)します。  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>アセンブリ、.NET Framework 4 用の Office 拡張機能で、 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 次の表は、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] と [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]の Office 拡張機能に含まれているアセンブリをまとめたものです。 名前空間とこれらのアセンブリの型に関するドキュメントについては、次を参照してください。[に関する管理リファレンス&#40;Visual Studio での Office 開発&#41;](../vsto/managed-reference-office-development-in-visual-studio.md)します。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|次の型を提供します。<br /><br /> リボンのカスタマイズとスマート タグを作成する型。 **注:**    スマート タグは、[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] で非推奨とされます。<br />ドキュメント レベルのカスタマイズと VSTO アドインのカスタム作業ウィンドウで、操作ウィンドウを作成するための型。|  
|Microsoft.Office.Tools.Excel.dll|Excel プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、次の[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)参照してください。|  
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できる型を提供します。|  
|Microsoft.Office.Tools.Word.dll|Word プロジェクトのホスト項目とホスト コントロールを表すインターフェイスとサポートする型を提供します。 詳細については、次を参照してください。[拡張オブジェクトを使用して Word の自動化](../vsto/automating-word-by-using-extended-objects.md)します。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|次の型を提供します。<br /><br /> -Visual Studio Tools for Office ランタイムによってスローされる例外。<br />フォーム領域の属性の Outlook を作成するときに使用することができます。|  
|Microsoft.Office.Tools.dll|Visual Studio Tools for Office Runtime インフラストラクチャに属し、コードから直接使用するものではない型を提供します。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性と<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>インターフェイスで、ドキュメント レベル カスタマイズでキャッシュ データ オブジェクトを使用することができます。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。<br />-<xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>インターフェイスで、Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できます。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)します。<br />-Visual Studio Tools for Office ランタイムによってスローされる例外。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の種類です。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスは、カスタマイズ アセンブリをドキュメントにアタッチして、キャッシュされたデータをドキュメントにアクセスするを使用することができます。 詳細については、次を参照してください。 [ServerDocument クラスを使用してサーバー上のドキュメントを管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)します。<br />、階層を表すいくつかのクラスには、ドキュメント レベル カスタマイズ内のデータがキャッシュされます。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)します。|  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトは次のアセンブリも参照します。 これらのアセンブリは再頒布可能な [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] に含まれません。 これらはむしろ、ソリューションで展開しなければならない従属アセンブリです。 既定では、プロジェクトのビルド出力フォルダーにコピーされます (これらのアセンブリの **[ローカル コピー]** プロパティは **True**に設定されます)。 ClickOnce を使用してプロジェクトを展開する場合、これらのアセンブリは生成されたパッケージに含まれます。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|VSTO アドイン プロジェクトで生成される `ThisAddIn` クラスとすべてのプロジェクトで生成される Ribbon クラスの基底クラスを提供します。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -基本、生成されたクラス`ThisWorkbook`と`Sheet`クラスのドキュメント レベル プロジェクトの Excel。<br />、Excel プロジェクトのワークシートで使用できる Windows フォーム コントロール。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Outlook プロジェクトで生成される `ThisAddIn` とフォーム領域クラスの基本クラスを提供します。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|次の型を提供します。<br /><br /> -基本、生成されたクラス`ThisDocument`Word のドキュメント レベル プロジェクト内のクラス。<br />、Word プロジェクト内のドキュメントで使用できる Windows フォーム コントロール。|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3.5 の Office 拡張機能アセンブリ  
 次の表は、.NET Framework 3.5 の Office 拡張機能に含まれているアセンブリをまとめたものです。 名前空間とこれらのアセンブリのクラスに関するドキュメントについては、Visual Studio 2008 ドキュメントのリファレンス セクションを参照してください: [ http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)します。  
  
|[アセンブリ名]|説明|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|次の型を提供します。<br /><br /> -Microsoft.Office.Tools.AddIn の基本クラス、VSTO アドイン。<br />リボンのカスタマイズとスマート タグを作成するためのクラスです。 **注:**    スマート タグは、[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] で非推奨とされます。<br />ドキュメント レベルのカスタマイズと VSTO アドインにおけるカスタム作業ウィンドウで、操作ウィンドウを作成するためのクラス。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Excel ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、次の[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)参照してください。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Outlook VSTO アドインでカスタム フォーム領域の作成に使用できるクラスを提供します。|  
|Microsoft.Office.Tools.Word.v9.0.dll|Word ソリューションのホスト項目とホスト コントロールを提供します。 詳細については、次を参照してください。[拡張オブジェクトを使用して Word の自動化](../vsto/automating-word-by-using-extended-objects.md)します。|  
|Microsoft.Office.Tools.v9.0.dll|次の型を提供します。<br /><br /> - [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90))クラスで、ホスト コントロールでドキュメント レベルのカスタマイズのデータ バインディング機能を提供します。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の種類です。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性と<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>インターフェイスで、ドキュメント レベル カスタマイズでキャッシュ データ オブジェクトを使用することができます。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。<br />-Visual Studio Tools for Office ランタイムによってスローされる例外。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の種類です。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Office ソリューションの ClickOnce インストーラーの最後の手順として追加のインストール手順を実行するために実装できる <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> インターフェイスを提供します。 詳細については、次を参照してください。[高度な Office ソリューションの配置](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100))します。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|次の型を提供します。<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスは、プログラムでカスタマイズ アセンブリをドキュメントにアタッチして、キャッシュされたデータをドキュメントにアクセスするを使用することができます。 詳細については、次を参照してください。 [ServerDocument クラスを使用してサーバー上のドキュメントを管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)します。<br />、階層を表すいくつかのクラスには、ドキュメント レベル カスタマイズ内のデータがキャッシュされます。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)します。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|次の型を提供します。<br /><br /> リストのエントリを Office に信頼を与えるユーザー信頼を作成するのに使用できる-Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry と Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList クラス.NET Framework 3.5 を対象とするソリューションです。<br />-Visual Studio Tools for Office runtime インフラストラクチャの一部であり、コードから直接使用するものではありませんその他の種類です。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のツール for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio のツール for Office runtime のインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  