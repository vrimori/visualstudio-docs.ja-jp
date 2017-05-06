---
title: "Office プライマリ相互運用機能アセンブリ"
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
  - "プライマリ相互運用機能アセンブリ"
  - "アセンブリ [Visual Studio での Office 開発]、プライマリ相互運用機能アセンブリ"
  - "Office プライマリ相互運用機能アセンブリ"
ms.assetid: aa29d12c-185f-4558-a7cd-3d85f924203d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Office プライマリ相互運用機能アセンブリ
  Office プロジェクトから Microsoft Office アプリケーションの機能を使用するには、アプリケーションのプライマリ相互運用機能アセンブリ \(PIA: Primary Interop Assembly\) を使用することが必要です。 PIA によって、Microsoft Office アプリケーションの COM ベースのオブジェクト モデルと対話するマネージ コードを作成できるようになります。  
  
 新しい Office プロジェクトを作成すると、Visual Studio により、そのプロジェクトのビルドに必要な PIA への参照が追加されます。 場合によっては、その他の PIA への参照を追加することが必要になります \(たとえば、Microsoft Office Excel 用のプロジェクトで Microsoft Office Word の機能を使用する場合など\)。  
  
 このトピックでは、Office プロジェクトでの Microsoft Office PIA の使用に関する次の側面について説明します。  
  
-   [プロジェクトをビルドして実行するためのプライマリ相互運用機能アセンブリ](#separateassemblies)  
  
-   [1 つのプロジェクトで複数の Microsoft Office アプリケーションの機能を使用する](#usingfeatures)  
  
-   [Microsoft Office アプリケーション プライマリ相互運用機能アセンブリの完全な一覧](#pialist)  
  
 プライマリ相互運用機能アセンブリの詳細については、「[プライマリ相互運用機能](http://msdn.microsoft.com/ja-jp/b977a8be-59a0-40a0-a806-b11ffba5c080)」を参照してください。  
  
##  <a name="separateassemblies"></a> プロジェクトをビルドして実行するためのプライマリ相互運用機能アセンブリ  
 Visual Studio では、開発用コンピューターで PIA のさまざまなセットを使用します。 これらのアセンブリ セットは、次の場所に配置されます。  
  
-   Program Files ディレクトリ下のフォルダー。  
  
     これらのアセンブリのコピーは、コードを記述してプロジェクトをビルドするときに使用されます。 これらのアセンブリは、Visual Studio によって自動的にインストールされます。  
  
-   グローバル アセンブリ キャッシュ  
  
     これらのアセンブリのコピーは、プロジェクトの実行やデバッグを行うときなど、一部の開発タスクで使用されます。 これらのアセンブリのインストールと登録は、Visual Studio では行われません。手動で行う必要があります。  
  
### Program Files ディレクトリ下のプライマリ相互運用機能アセンブリ  
 Visual Studio をインストールすると、ファイル システム内の場所 \(グローバル アセンブリ キャッシュ外部\) に PIA が自動的にインストールされます。 新しいプロジェクトを作成すると、Visual Studio により、これらの PIA のコピーへの参照がプロジェクトに自動的に追加されます。 Visual Studio は、グローバル アセンブリ キャッシュ内のアセンブリではなく、これらの PIA のコピーを使用して、プロジェクトの開発やビルドを行うときに型参照を解決します。  
  
 PIA のコピーを使用することで、Visual Studio は、異なるバージョンの PIA がグローバル アセンブリ キャッシュに登録されている場合に発生することのある開発上の問題を回避できます。  
  
 Visual Studio は、開発用コンピューターの次の場所に、PIA のコピーをインストールします。  
  
-   %ProgramFiles%\\Microsoft Visual Studio 12.0\\Visual Studio Tools for Office\\PIA\\Office14  
  
     \(または、64 ビット オペレーティング システムでは %ProgramFiles\(x86\)%\\Microsoft Visual Studio 12.0\\Visual Studio Tools for Office\\PIA\\Office14\)  
  
-   %ProgramFiles%\\Microsoft Visual Studio 12.0\\Visual Studio Tools for Office\\PIA\\Office15  
  
     \(または、64 ビット オペレーティング システムでは %ProgramFiles\(x86\)%\\Microsoft Visual Studio 12.0\\Visual Studio Tools for Office\\PIA\\Office15\)  
  
### グローバル アセンブリ キャッシュ内のプライマリ相互運用機能アセンブリ  
 開発タスクを実行するには、開発用コンピューターのグローバル アセンブリ キャッシュに PIA をインストールし、登録する必要があります。 通常、開発用コンピューターに Office をインストールすると、自動的に PIA がインストールされます。 詳細については、「[Office ソリューションを開発できるようにコンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)」を参照してください。  
  
 Office PIA は、 Office ソリューションを実行するエンド ユーザーのコンピューターには必要ありません。 詳細については、「[Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)」を参照してください。  
  
##  <a name="usingfeatures"></a> 単一のプロジェクトで複数の Microsoft Office アプリケーションの機能を使用する  
 Visual Studio の各 Office プロジェクト テンプレートは、単一の Microsoft Office アプリケーションと連動するようになっています。 複数の Microsoft Office アプリケーションの機能を使用したり、Visual Studio 内にプロジェクトが含まれないアプリケーションやコンポーネントの機能を使用したりするには、必要な PIA への参照を追加しなければなりません。  
  
 ほとんどの場合、Visual Studio によって %ProgramFiles%\\Microsoft Visual Studio 12.0\\Visual Studio Tools for Office\\PIA\\ ディレクトリにインストールされる PIA への参照を追加することが必要になります。 これらのバージョンのアセンブリは、**\[参照マネージャー\]** ダイアログ ボックスの **\[フレームワーク\]** タブに表示されます。 詳細については、「[方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)」を参照してください。  
  
 グローバル アセンブリ キャッシュに PIA をインストールして登録すると、これらのバージョンのアセンブリは、**\[参照マネージャー\]** ダイアログ ボックスの **\[COM\]** タブに表示されます。 これらのバージョンのアセンブリを使用すると開発上の問題が発生するため、これらのアセンブリに参照を追加することは避ける必要があります。 たとえば、異なるバージョンの PIA がグローバル アセンブリ キャッシュに登録されている場合、**\[参照マネージャー\]** ダイアログ ボックスの **\[COM\]** タブで別のバージョンのアセンブリを指定しても、プロジェクトは最後に登録されたバージョンのアセンブリにバインドします。  
  
> [!NOTE]  
>  アセンブリによっては、参照元のアセンブリを追加すると、参照先のアセンブリも自動的に追加される場合があります。 たとえば、Word、Excel、Outlook、Microsoft Forms、または Graph アセンブリへの参照を追加すると、アセンブリの Office.dll と Microsoft.Vbe.Interop.dll への参照も自動的に追加されます。  
  
##  <a name="pialist"></a> Microsoft Office アプリケーション プライマリ相互運用機能アセンブリ  
 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] と [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] で利用できるプライマリ相互運用機能アセンブリの一覧を次の表に示します。  
  
|Office アプリケーションまたはコンポーネント|プライマリ相互運用機能アセンブリの名前|  
|-------------------------------|-------------------------|  
|Microsoft Access 14.0 Object Library<br /><br /> Microsoft Access 15.0 Object Library|Microsoft.Office.Interop.Access.dll|  
|Microsoft Office 14.0 Access Database Engine Object Library<br /><br /> Microsoft Office 15.0 Access Database Engine Object Library|Microsoft.Office.Interop.Access.Dao.dll|  
|Microsoft Excel 14.0 Object Library<br /><br /> Microsoft Excel 15.0 Object Library|Microsoft.Office.Interop.Excel.dll|  
|Microsoft Graph 14.0 Object Library \(PowerPoint、Access、および Word のグラフで使用\)<br /><br /> Microsoft Graph 15.0 Object Library|Microsoft.Office.Interop.Graph.dll|  
|Microsoft InfoPath 2.0 Type Library \(InfoPath 2007 専用\)|Microsoft.Office.Interop.InfoPath.dll|  
|Microsoft InfoPath XML 相互運用機能アセンブリ \(InfoPath 2007 専用\)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Microsoft Office 14.0 Object Library \(Office の共有機能\)<br /><br /> Microsoft Office 15.0 Object Library \(Office の共有機能\)|office.dll|  
|Microsoft Office Outlook View Control \(受信トレイにアクセスする Web ページおよびアプリケーションで使用可能\)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Microsoft Outlook 14.0 Object Library<br /><br /> Microsoft Outlook 15.0 Object Library|Microsoft.Office.Interop.Outlook.dll|  
|Microsoft PowerPoint 14.0 Object Library<br /><br /> Microsoft PowerPoint 15.0 Object Library|Microsoft.Office.Interop.PowerPoint.dll|  
|Microsoft Project 14.0 Object Library<br /><br /> Microsoft Project 15.0 Object Library|Microsoft.Office.Interop.MSProject.dll|  
|Microsoft Publisher 14.0 Object Library<br /><br /> Microsoft Publisher 15.0 Object Library|Microsoft.Office.Interop.Publisher.dll|  
|Microsoft SharePointDesigner 14.0 Web Object Reference Library|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Microsoft SharePointDesigner 14.0 Page Object Reference Library|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Microsoft Smart Tags 2.0 Type Library **Note:**  スマート タグは、[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] および [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] では使用されていません。|Microsoft.Office.Interop.SmartTag.dll|  
|Microsoft Visio 14.0 Type Library<br /><br /> Microsoft Visio 15.0 Type Library|Microsoft.Office.Interop.Visio.dll|  
|Microsoft Visio 14.0 Save As Web Type Library<br /><br /> Microsoft Visio 15.0 Save As Web Type Library|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Microsoft Visio 14.0 Drawing Control Type Library<br /><br /> Microsoft Visio 15.0 Drawing Control Type Library|Microsoft.Office.Interop.VisOcx.dll|  
|Microsoft Word 14.0 Object Library<br /><br /> Microsoft Word 15.0 Object Library|Microsoft.Office.Interop.Word.dll|  
|Microsoft Visual Basic for Applications Extensibility 5.3|Microsoft.Vbe.Interop.dll|  
  
### バインディング リダイレクト アセンブリ  
 グローバル アセンブリ キャッシュに \(Office と共に、または PIA の再頒布可能パッケージをインストールすることにより\) Office PIA をインストールし、登録すると、同時にバインディング リダイレクト アセンブリがグローバル アセンブリ キャッシュだけにインストールされます。 これらのアセンブリにより、実行時にプライマリ相互運用機能アセンブリの正しいバージョンが確実に読み込まれます。 たとえば、[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] アセンブリを参照するソリューションが、同じプライマリ相互運用機能アセンブリの [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] バージョンがあるコンピューターで実行されると、バインド リダイレクト アセンブリによって、そのプライマリ相互運用機能アセンブリの [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] バージョンを読み込むように [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ランタイムに指示されます。 詳細については、「[方法: 自動バインディング リダイレクトを有効&#47;無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Binding%20Redirection.md)」を参照してください。  
  
## 参照  
 [方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [InfoPath ソリューション](../vsto/infopath-solutions.md)   
 [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)   
 [PowerPoint ソリューション](../vsto/powerpoint-solutions.md)   
 [Project ソリューション](../vsto/project-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [全般リファレンス &#40;Visual Studio での Office 開発&#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  