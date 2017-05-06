---
title: "Office ソリューションのアップグレードと移行"
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
  - "Office アプリケーション [Visual Studio での Office 開発]、アップグレード"
  - "Office プロジェクト [Visual Studio での Office 開発]、アップグレード"
  - "アップグレード (アプリケーションを) [Visual Studio での Office 開発]"
  - "アップグレード (Visual Studio の Office ソリューションを)"
  - "移行 (Visual Studio の Office ソリューションを)"
ms.assetid: cc60cdcb-593d-498a-8358-f1f3ac673fe1
caps.latest.revision: 105
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 101
---
# Office ソリューションのアップグレードと移行
  旧バージョンの Visual Studio で作成された Microsoft Office プロジェクトがある場合、現在のバーションの Visual Studio で使用するには、そのプロジェクトをアップグレードする必要があります。 Microsoft Office プロジェクトをアップグレードするには、Microsoft Office 開発ツールが含まれているバージョンの Visual Studio でそれを開きます。 Microsoft Office 開発ツールを含む Visual Studio のバージョンの詳細については、「[Office ソリューションを開発できるようにコンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)」を参照してください。  
  
> [!NOTE]  
>  Visual Studio では、以前のバージョンの Visual Studio を使用して作成した InfoPath フォーム テンプレート プロジェクトはアップグレードできません。 これらの種類のプロジェクトは、Visual Studio の現在のリリースではサポートされていません。  
  
## アップグレードされたプロジェクトに対する変更  
 Microsoft Office プロジェクトをアップグレードするときに、次の項目を対象とするプロジェクトが Visual Studio によって変更されます。  
  
-   Visual Studio 2010 Tools for Office Runtime。 詳細については、「[Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
-   現在のアセンブリ参照。  
  
-   このプロジェクトの種類でサポートされている .NET Framework のバージョン \(Visual Studio 2013 にアップグレードする場合のみ\)。  
  
-   このプロジェクトの種類でサポートされている Microsoft Office のバージョン \(Visual Studio 2013 にアップグレードする場合のみ\)。  
  
## アセンブリ参照  
 Visual Studio は、プロジェクト内の次のアセンブリ参照をアップグレードします。  
  
-   Microsoft Office プライマリ相互運用機能アセンブリ \(PIA\)。  
  
-   [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] のアセンブリ。 これらのアセンブリの詳細については、「[Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
-   依存アセンブリの新バージョンまたは更新バージョン。  
  
## 対象の .NET Framework  
 プロジェクトを Visual Studio 2013 にアップグレードすると、Visual Studio は [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] または [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とするようにプロジェクトを変更します。 プロジェクトが対象とする .NET Framework のバージョンは、自分のコンピューターにインストールされている Office のバージョンによって異なります。[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] がインストールされている場合は、[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするように Visual Studio によってプロジェクトが変更されます。 それ以外の場合は、Visual Studio は [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とするようにプロジェクトを変更します。  
  
> [!NOTE]  
>  対象を変更されたソリューションを実行するために、開発用コンピューターとエンド ユーザーのコンピューターでいくつかの追加の手順が必要になることがあります。また、特定の機能を使用するプロジェクトはコンパイルされなくなります。 詳細については、「[.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)」を参照してください。  
  
 Office プロジェクトで [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする場合は、.NET Framework 3.5 を対象とする場合には使用できないいくつかの機能を使用できます。 詳細については、「[Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)」を参照してください。  
  
## 対象の Office アプリケーション  
 Office プロジェクトを Visual Studio 2013 にアップグレードすると、Visual Studio はプロジェクトの種類 \(ドキュメント レベルのカスタマイズ プロジェクトや VSTO アドイン プロジェクトなど\) によってサポートされている Microsoft Office のバージョンを対象とするようにプロジェクトを変更します。  
  
 Visual Studio 2013 の Office プロジェクトは、[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] と [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] のアプリケーションを対象とすることができます。 Visual Studio はインストールされている Office の最新バージョンを対象とするようにプロジェクトを変更します。 Office のどのバージョンもインストールされていない場合、Visual Studio はプロジェクトをアップグレードしません。  
  
> [!NOTE]  
>  [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 以降を対象とするように VSTO アドイン プロジェクトをアップグレードする場合は、VSTO アドインの `ThisAddIn_Startup` イベント ハンドラーにアプリケーション内のドキュメントにアクセスするコードが含まれていないことを確認してください。 詳細については、「[Office アプリケーションの起動時にドキュメントにアクセスする](../vsto/programming-vsto-add-ins.md#AccessingDocuments)」を参照してください。  
  
 ドキュメント レベルのカスタマイズの場合、[!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] は、.xls や .doc の拡張子を持つドキュメントなど、バイナリ形式のプロジェクト内にあるドキュメントを、Office Open XML ファイル形式に変換します。 Open XML の詳細については、「[新しいファイル名拡張子および Open XML 形式入門](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1)」を参照してください。  
  
> [!NOTE]  
>  スマート タグは Excel 2010 および Word 2010 では使用されていません。 したがって、ソリューションでスマート タグを使用している場合は、Visual Studio 2013 または Visual Studio 2015 でソリューションをテストおよびデバッグするために、それらを削除する必要があります。  
  
## Microsoft Office 2003 プロジェクトのアップグレード  
 Microsoft Office 2003 を対象とするドキュメント レベルのカスタマイズおよび VSTO アドインをアップグレードする際には、追加の考慮事項がいくつかあります。  
  
### ドキュメント レベルのプロジェクト  
 プロジェクトのドキュメントに Windows フォーム コントロールが含まれている場合は、プロジェクトをアップグレードする前に、Visual Studio 2005 Tools for Office Second Edition Runtime がインストールされている必要もあります。 プロジェクトをアップグレードする前に、このバージョンのランタイムが開発用コンピューターにインストールされていない場合は、アップグレード後のプロジェクトでコンパイル エラーまたは実行時エラーが発生することがあります。 Visual Studio 2005 Tools for Office Second Edition Runtime は、他の Office ソリューションで使用されていない場合、プロジェクトのアップグレードが完了した後に開発用コンピューターからアンインストールできます。 このバージョンのランタイムは、Microsoft ダウンロード センターの「[Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime \(VSTO 2005 SE\) \(x86\)](http://go.microsoft.com/fwlink/?linkid=49612)」から再頒布可能パッケージとしてダウンロードできます。  
  
### VSTO アドイン プロジェクト  
 元のプロジェクトのソリューション ファイルに、VSTO アドインをインストールするように構成されたセットアップ プロジェクトまたは InstallShield Limited Edition プロジェクトが含まれていた場合、Visual Studio はそのプロジェクトをアップグレードしますが、プロジェクトに対してそれ以外の変更は加えません。 引き続き Windows インストーラー ファイルを使用して VSTO アドインを配置するには、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]、Visual Studio 2010 Tools for Office Runtime、および必要な場合は VSTO アドインで参照されているプライマリ相互運用機能アセンブリなど、新しい必須コンポーネントをインストールするようにセットアップ プロジェクトまたは InstallShield Limited Edition プロジェクトを変更する必要があります。 詳細については、「[Windows インストーラーを使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)」を参照してください。  
  
 ClickOnce を使用して VSTO アドインを配置する場合には、セットアップ プロジェクトまたは InstallShield Limited Edition プロジェクトを完全に削除できます。 ClickOnce を使用した VSTO アドインの配置の詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
## 参照  
 [方法: Office ソリューションをアップグレードする](http://msdn.microsoft.com/ja-jp/a269e539-b717-4680-a568-2152b070347e)   
 [.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [&#91;プロジェクトのアップグレード&#93; &#40;&#91;オプション&#93; ダイアログ ボックス&#41;](../vsto/project-upgrade-options-dialog-box.md)  
  
  