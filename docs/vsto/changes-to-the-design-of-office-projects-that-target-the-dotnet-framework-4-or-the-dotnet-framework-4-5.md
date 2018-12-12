---
title: .NET Framework を対象にする Office プロジェクトのデザインの変更します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b200c5b0df5f150e0d34b351a3e36a8a986f3ed6
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248245"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Office プロジェクトの設計を対象とする .NET Framework 4 または .NET Framework 4.5 に変更します。
  [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]以降の Visual Studio では、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする Office プロジェクトのデザインに対していくつかの変更が導入されました。 以前のバージョンの Visual Studio の Office プロジェクトに慣れている場合は、これらの変更内容を確認してから、.NET Framework 4.0 以降のこれらのバージョンを対象とする Office プロジェクトを開発してください。 既定では、Visual Studio 2013 以降を使用して作成したすべてのプロジェクトは、.NET Framework 4.0 以降が対象になります。  
  
 次のセクションでは、これらの Office プロジェクトのデザインの変更について説明します。  
  
## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Visual Studio 2010 Tools for Office ランタイムのインターフェイスに基づくデザインを理解します。  
 対象とする Office プロジェクトを開発する際に、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]後で、ほとんどのでは、Visual Studio 2010 Tools for Office ランタイムを使用する型がインターフェイスです。 これは、以前のバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]からの重大な変更点です。以前のバージョンでは、これらの型はクラスです。 たとえば、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする場合、 <xref:Microsoft.Office.Tools.Excel.Worksheet> と <xref:Microsoft.Office.Tools.Word.Document> の型はクラスではなくインターフェイスです。 詳細については、次を参照してください。 [Visual Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)します。  
  
 以前のバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] で直接インスタンス化できた型の場合は、`Globals.Factory` オブジェクトのメソッドを使用して型のインスタンスを取得できます。 たとえば、<xref:Microsoft.Office.Tools.Excel.SmartTag> インターフェイスを実装するオブジェクトを取得するには、`Globals.Factory.CreateSmartTag` メソッドを使用します。 詳細については、次のトピックを参照してください。  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Excel および Word プロジェクトを更新します。](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズを更新します。](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [.NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域を更新します。](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Office プロジェクトに新しい基本クラス  
 Visual Studio 2010 Tools for Office ランタイムの新しいインターフェイス ベースのデザインなど、Office プロジェクトで生成されるクラスに影響`ThisDocument`、 `ThisWorkbook`、および`ThisAddIn`します。 .NET Framework 3.5 および以前のバージョンのフレームワークを対象とする Office プロジェクトでは、これらの生成されるクラスは、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、`Microsoft.Office.Tools.Word.Document`、`Microsoft.Office.Tools.Excel.Worksheet` などの `Microsoft.Office.Tools.AddIn` のクラスから派生します。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、これらの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] クラスがインターフェイスになりました。 そのため、Office プロジェクトで生成されるクラスでは実装を派生できなくなりました。 代わりに、生成されるクラスは、 <xref:Microsoft.Office.Tools.Word.DocumentBase>、 <xref:Microsoft.Office.Tools.Excel.WorksheetBase>、 <xref:Microsoft.Office.Tools.AddInBase>などの新しい基底クラスから派生します。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)と[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)します。  
  
 基底クラスは、再頒布可能な [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には含まれません。 代わりに、Visual Studio に含まれるユーティリティ アセンブリに定義されています。 これらのアセンブリは、Office プロジェクトのビルド時に出力フォルダーにコピーし、ソリューションと共に配置する必要があります。 ユーティリティ アセンブリについての詳細については、次を参照してください。 [、Visual Studio Tools for Office ランタイムのアセンブリ](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)します。  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>.NET Framework 4 に再ターゲットされた Office プロジェクトにおける重大な変更  
 次の表では、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に対象が変更された Office プロジェクトの互換性に影響する主な変更点を示します。 詳細については、次を参照してください。[以降、.NET Framework 4 への移行 Office ソリューション](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)します。  
  
|互換性に影響する変更点|結果|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> が Office プロジェクトで使用またはサポートされなくなりました。|Visual Studio 2008 からアップグレードする Office プロジェクトの AssemblyInfo コード ファイルからこの属性を削除する必要があります。 詳細については、次を参照してください。 [、.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの実行に変更が必要な](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)します。|  
|**ExcelLocale1033Attribute**が不要になったために使用または Excel プロジェクトではサポートされています。|この属性を削除する必要があります、 *AssemblyInfo* Excel プロジェクトのコード ファイル。 詳細については、次を参照してください。[更新 Excel および Word プロジェクト、.NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)します。|  
|**リボン (ビジュアルなデザイナー)** プロジェクト項目のプログラミング モデルが変更されました。|プロジェクトのすべてのリボン項目の分離コード ファイルを変更する必要があります。 実行時にリボン コントロールをインスタンス化、リボン イベントを処理またはリボン コンポーネントの位置をプログラムによって設定するすべてのコードを変更することも必要があります。 詳細については、次を参照してください。 [、.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの更新プログラムのリボンのカスタマイズ](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)します。|  
|Outlook フォーム領域のプログラミング モデルが変更されました。|プロジェクトとそのコードを実行時に特定のフォーム領域クラスをインスタンス化では、フォーム領域の分離コード ファイルを変更する必要があります。 詳細については、次を参照してください。 [、.NET Framework 4 または .NET Framework 4.5 に移行する Outlook プロジェクトのフォーム領域を更新](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)します。|  
|Excel プロジェクトと Word プロジェクトでのスマート タグのプログラミング モデルが変更されました。 スマート タグは、[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] で非推奨とされます。|ソリューションでスマート タグを使用している場合は、プロジェクトをビルドするときにエラーが発生します。 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] ではスマート タグが非推奨とされているため、[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 以降でソリューションをテストおよびデバッグするには、タグを削除する必要があります。|  
|`GetVstoObject` メソッドと `HasVstoObject` メソッドの構文が変更されました。|プライマリ相互運用機能アセンブリ (PIA) からネイティブ オブジェクトでこれらのメソッドにアクセスするときに、`Globals.Factory` オブジェクトをメソッドに渡す必要があります。または、プロジェクトの `Globals.Factory` プロパティによって返されるオブジェクトでこれらのメソッドにアクセスすることもできます。 詳細については、次を参照してください。[更新 Excel および Word プロジェクト、.NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)します。|  
|Word コンテンツ コントロールのイベントが新しいデリゲートに関連付けられています。|Word コンテンツ コントロールのイベントを処理するすべてのコードを変更し、新しいデリゲートを指定する必要があります。 詳細については、次を参照してください。[更新 Excel および Word プロジェクト、.NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)します。|  
|`OLEObject` クラスと `OLEControl` クラスの名前が変更されました。|これらのクラスのインスタンスを使用するすべてのコードを変更し、代わりに <xref:Microsoft.Office.Tools.Excel.ControlSite> オブジェクトまたは <xref:Microsoft.Office.Tools.Word.ControlSite> オブジェクトを使用する必要があります。 詳細については、次を参照してください。[更新 Excel および Word プロジェクト、.NET Framework 4 または .NET Framework 4.5 に移行する](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)します。|  
|ホスト項目クラスをなど`ThisWorkbook`、 `Sheet` *n*、 `ThisDocument`、および`ThisAddIn`、提供されなくなります、`Dispose`メソッドをオーバーライドすることができます。|`Dispose` メソッド オーバーライドのすべてのコードをホスト項目クラス (`Shutdown` など) の `ThisAddIn_Shutdown` イベント ハンドラーに移動し、ホスト項目クラスから `Dispose` メソッド オーバーライドを削除する必要があります。|  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework 4 またはそれ以降の Office ソリューションを移行します。](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [新機能の Office 開発の新機能](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio のツール for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  