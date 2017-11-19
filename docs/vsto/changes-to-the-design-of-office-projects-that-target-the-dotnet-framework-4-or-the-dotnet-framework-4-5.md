---
title: ".NET Framework 4 または .NET Framework 4.5 を対象とする Office プロジェクトのデザインの変更 |Microsoft ドキュメント"
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
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
ms.assetid: 290f5cb4-e2ee-4ed8-987c-2f013405cee9
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbf93e29e9bde2029bfff262a953d5858f17d084
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 または .NET Framework 4.5 を対象とする Office プロジェクトのデザインの変更
  [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]以降の Visual Studio では、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする Office プロジェクトのデザインに対していくつかの変更が導入されました。 以前のバージョンの Visual Studio の Office プロジェクトに慣れている場合は、これらの変更内容を確認してから、.NET Framework 4.0 以降のこれらのバージョンを対象とする Office プロジェクトを開発してください。 既定では、Visual Studio 2013 以降を使用して作成したすべてのプロジェクトは、.NET Framework 4.0 以降が対象になります。  
  
 次のセクションでは、これらの Office プロジェクトのデザインの変更について説明します。  
  
## <a name="understanding-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Visual Studio 2010 Tools for Office Runtime のインターフェイス ベースのデザインについて  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする Office プロジェクトを開発する際に、Visual Studio 2010 Tools for Office Runtime で最もよく使用する型はインターフェイスです。 これは、以前のバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]からの重大な変更点です。以前のバージョンでは、これらの型はクラスです。 たとえば、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする場合、 <xref:Microsoft.Office.Tools.Excel.Worksheet> と <xref:Microsoft.Office.Tools.Word.Document> の型はクラスではなくインターフェイスです。 詳細については、「 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
 以前のバージョンので直接インスタンス化できた型の[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、これらの型のインスタンスを取得、Globals.Factory オブジェクトのメソッドを使用するようになりました。 たとえばを実装するオブジェクトを取得するため、<xref:Microsoft.Office.Tools.Excel.SmartTag>インターフェイスでは、Globals.Factory.CreateSmartTag メソッドを使用します。 詳細については、次のトピックを参照してください。  
  
-   [更新の Excel および Word プロジェクトの .NET Framework 4 または .NET Framework 4.5 に移行します。](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズの更新](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域の更新](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Office プロジェクトの新しい基底クラス  
 Visual Studio 2010 Tools for Office Runtime の新しいインターフェイス ベースのデザインは、Office プロジェクトで生成される `ThisDocument`、 `ThisWorkbook`、 `ThisAddIn`などのクラスに影響します。 .NET Framework 3.5 と以前のバージョンの framework を対象とする Office プロジェクトで、これらの生成されたクラスがクラスから派生、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Microsoft.Office.Tools.Word.Document、Microsoft.Office.Tools.Excel.Worksheet などとMicrosoft.Office.Tools.AddIn です。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、これらの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] クラスがインターフェイスになりました。 そのため、Office プロジェクトで生成されるクラスでは実装を派生できなくなりました。 代わりに、生成されるクラスは、 <xref:Microsoft.Office.Tools.Word.DocumentBase>、 <xref:Microsoft.Office.Tools.Excel.WorksheetBase>、 <xref:Microsoft.Office.Tools.AddInBase>などの新しい基底クラスから派生します。 詳細については、次のトピックを参照してください。 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md) および [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 基底クラスは、再頒布可能な [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には含まれません。 代わりに、Visual Studio に含まれるユーティリティ アセンブリに定義されています。 これらのアセンブリは、Office プロジェクトのビルド時に出力フォルダーにコピーし、ソリューションと共に配置する必要があります。 ユーティリティ アセンブリについて詳しくは、「 [Assemblies in the Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)」をご覧ください。  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>.NET Framework 4 に再ターゲットされた Office プロジェクトの互換性に影響する変更点  
 次の表では、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に対象が変更された Office プロジェクトの互換性に影響する主な変更点を示します。 詳しくは、「 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)」をご覧ください。  
  
|互換性に影響する変更点|結果|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> が Office プロジェクトで使用またはサポートされなくなりました。|Visual Studio 2008 からアップグレードする Office プロジェクトの AssemblyInfo コード ファイルからこの属性を削除する必要があります。 詳細については、次を参照してください。[実行 Office プロジェクトは .NET Framework 4 または .NET Framework 4.5 に移行するのに必要な変更](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。|  
|ExcelLocale1033Attribute が使用または Excel プロジェクトではサポートされなくです。|Excel プロジェクトの AssemblyInfo コード ファイルからこの属性を削除する必要があります。 詳細については、次を参照してください。[更新の Excel および Word プロジェクトの .NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。|  
|**リボン (ビジュアルなデザイナー)** プロジェクト項目のプログラミング モデルが変更されました。|プロジェクトのすべてのリボン項目の分離コード ファイルを変更する必要があります。 また、実行時にリボン コントロールをインスタンス化するコード、リボン イベントを処理するコード、またはリボン コンポーネントの位置をプログラムによって設定するコードをすべて変更する必要があります。 詳細については、次を参照してください。 [Office のリボンのカスタマイズの更新プロジェクトを移行するには、.NET Framework 4 または .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。|  
|Outlook フォーム領域のプログラミング モデルが変更されました。|プロジェクトのフォーム領域の分離コード ファイル、および実行時に特定のフォーム領域クラスをインスタンス化するすべてのコードを変更する必要があります。 詳細については、次を参照してください。 [Outlook でフォーム領域の更新プロジェクトを移行するには、.NET Framework 4 または .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。|  
|Excel プロジェクトと Word プロジェクトでのスマート タグのプログラミング モデルが変更されました。 スマート タグは、 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]では使用されていません。|ソリューションでスマート タグを使用している場合は、プロジェクトをビルドするときにエラーが発生します。 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]ではスマート タグが非推奨となっているため、 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 以降でソリューションをテストおよびデバッグするには、タグを削除する必要があります。|  
|Getvstoobject メソッドと HasVstoObject メソッドの構文が変更されました|プライマリ相互運用機能アセンブリ (Pia) からのネイティブ オブジェクトにアクセスすると、プロジェクト内の Globals.Factory プロパティによって返されるオブジェクトでこれらのメソッドにアクセスすることができます、これらのメソッドに Globals.Factory オブジェクトを渡す必要があります。 詳細については、次を参照してください。[更新の Excel および Word プロジェクトの .NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。|  
|Word コンテンツ コントロールのイベントが新しいデリゲートに関連付けられています。|Word コンテンツ コントロールのイベントを処理するすべてのコードを変更し、新しいデリゲートを指定する必要があります。 詳細については、次を参照してください。[更新の Excel および Word プロジェクトの .NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。|  
|OLEObject クラスと OLEControl クラスを名前変更されています。|これらのクラスのインスタンスを使用するすべてのコードを変更し、代わりに <xref:Microsoft.Office.Tools.Excel.ControlSite> オブジェクトまたは <xref:Microsoft.Office.Tools.Word.ControlSite> オブジェクトを使用する必要があります。 詳細については、次を参照してください。[更新の Excel および Word プロジェクトの .NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)です。|  
|ホスト項目クラスをなど`ThisWorkbook`、 `Sheet`  *n* 、 `ThisDocument`、および`ThisAddIn`、提供されなくなります Dispose メソッドをオーバーライドすることができます。|必要がありますに移動するすべてのコード Dispose メソッドのオーバーライドで、ホスト項目クラス内にシャット ダウン イベント ハンドラーなど、 `ThisAddIn_Shutdown`、し、ホスト項目クラスから Dispose メソッドのオーバーライドを削除します。|  
  
## <a name="see-also"></a>関連項目  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Office 開発の新機能](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  