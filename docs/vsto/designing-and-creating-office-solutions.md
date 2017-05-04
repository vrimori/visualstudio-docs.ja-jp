---
title: "Office ソリューションのデザインと作成 | Microsoft Docs"
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
  - "Visual Studio での Office 開発, 作成 (ソリューションを)"
  - "Visual Studio の Office プロジェクトの種類"
  - "Office ソリューション [Visual Studio での Office 開発], 作成"
  - "ソリューション [Visual Studio での Office 開発], 作成"
ms.assetid: 53c32c61-3d3a-4427-a5a7-f9c2c8f1de02
caps.latest.revision: 103
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 99
---
# Office ソリューションのデザインと作成
  Visual Studio には、さまざまな種類の Office ソリューションの作成に使用できるプロジェクト テンプレートが用意されています。  ここでは、プロジェクト テンプレートについて説明し、Office プロジェクトを作成するためのガイダンスを示します。  プロジェクトを作成した後でコードやユーザー インターフェイスのカスタマイズを実装する方法の詳細については、「[Office ソリューションの開発](../vsto/developing-office-solutions.md)」を参照してください。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Office プロジェクトの作成  
 開始する前に、要件を決定し、最適なソリューションの種類を探します。  たとえば、アプリケーションを使用するたびに作成した Office ソリューションを実行する必要がある場合は、VSTO アドインが最適です。  コードが 1 つのドキュメントと緊密に統合されている場合は、ドキュメント レベルのカスタマイズを作成します。  これらのプロジェクト タイプは、Visual Studio のプロジェクト テンプレートとして利用できます。  Visual Studio に付属している Office プロジェクト テンプレートの詳細については、「[Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)」を参照してください。  Office プロジェクトを作成する方法の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
 Office プロジェクトには、Visual Studio の他の種類のプロジェクトとは異なる機能とプロジェクト項目があります。  たとえば、ドキュメント レベルのプロジェクトを作成した場合は、プロジェクト内の文書またはブックを Visual Studio 内部で開いて編集できます。  詳細については、「[Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)」を参照してください。  
  
## .NET Framework のバージョンの選択  
 要件に最適なプロジェクトの種類を選択した後に、開発工程で使用する .NET Framework のバージョンを選択できます。  Office プロジェクトでは、次のバージョンの .NET Framework を対象にすることができます。  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 ソリューションを実行するエンド ユーザーのコンピューターには、プロジェクト用に選択した .NET Framework のバージョンが必要です。  たとえば、プロジェクトが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象としている場合、エンド ユーザーのコンピューターには [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] が必要です。  この例では、エンド ユーザーのコンピューターに .NET Framework 3.5 しかインストールされていない場合、ソリューションは実行されません。  
  
 .NET Framework 3.5 を対象とする VSTO アドイン プロジェクトを移行する場合、インストールした Office のバージョンに応じて、Visual Studio によってプロジェクトのターゲット フレームワークが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更されます。  
  
 ただし、プロジェクトで特定の機能を使用している場合は、Visual Studio によるターゲット フレームワークの変更後に、プロジェクトのコードの一部を変更することが必要になる場合があります。  対象となるフレームワークを変更する方法については、「[方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)」を参照してください。  プロジェクトで変更する必要がある点の詳細については、「[.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)」を参照してください。  
  
 Visual Studio によってプロジェクトの対象となる .NET Framework が変更されている場合に、ClickOnce を使用してソリューションを配置する場合は、**\[必須コンポーネント\]** ダイアログ ボックスで、対応するバージョンの .NET Framework も選択してください。  プロジェクトのターゲット フレームワークを変更しても、この選択内容は自動的には変わりません。  詳細については、「[方法: Office ソリューションを実行するための必須コンポーネントをエンド ユーザーのコンピューターにインストールする](http://msdn.microsoft.com/ja-jp/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)」を参照してください。  
  
> [!NOTE]  
>  .NET Framework 3.5 以前を [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] を使用して作成した Office プロジェクトの対象にすることはできません。  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] を使用して作成した Office プロジェクトには、[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] で導入された機能が必要です。  
  
### エンド ユーザーのコンピューターで Office PIA が必要な場合について  
 既定では、プロジェクトの各 Office PIA 参照の **\[相互運用型の埋め込み\]** プロパティが **\[True\]** \(これが既定値です\) に設定されているときは、エンド ユーザーのコンピューターに Office プライマリ相互運用機能アセンブリ \(PIA: Primary Interop Assembly\) がインストールされている必要はありません。  この場合、プロジェクトをビルドすると、ソリューションが使用する PIA 型の型情報がソリューション アセンブリに埋め込まれます。  実行時に、埋め込まれた型情報が PIA の代わりに使用され、Office アプリケーションの COM ベースのオブジェクト モデルが呼び出されます。  PIA の型をソリューションに埋め込む方法の詳細については、「[型の等価性と埋め込まれた相互運用機能型](../Topic/Type%20Equivalence%20and%20Embedded%20Interop%20Types.md)」を参照してください。  
  
 プロジェクトの各 Office PIA 参照の **\[相互運用型の埋め込み\]** プロパティが **\[False\]** に設定されている場合、ソリューションを実行する各エンド ユーザーのコンピューター上のグローバル アセンブリ キャッシュに Office PIA をインストールし、登録しておく必要があります。  ほとんどの場合、PIA は既定で Office と共にインストールされますが、ソリューションの必須コンポーネントとして再頒布可能な PIA を含めることもできます。  詳細については、「[Office ソリューションを配置するための必須コンポーネント](http://msdn.microsoft.com/ja-jp/9f672809-43a3-40a1-9057-397ce3b5126e)」を参照してください。  
  
### Client Profile について  
 .NET Framework Client Profile は、完全な .NET Framework のサブセットです。  .NET Framework のクライアント機能のみを使用し、Office ソリューションをできる限り迅速に配置する必要がある場合は、.NET Framework Client Profile を対象にすることができます。  詳細については、「[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)」を参照してください。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とする Office プロジェクトを作成するときに、既定で [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] が対象となります。 完全な [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 用に開発する場合は、プロジェクトを作成した後でこのオプションを設定する必要があります。  詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)」を参照してください。  
  
## Microsoft Office 64 ビット エディション用のソリューションの作成  
 Microsoft Office には、64 ビットと 32 ビットのエディションがあります。  両方のエディションで実行できる Office ソリューションを作成するには、プロジェクトのプラットフォーム ターゲット設定を **Any CPU** に設定する必要があります。  これは、Office プロジェクトの既定値です。 詳細については、「[Office ソリューションのビルド](../vsto/building-office-solutions.md)」を参照してください。  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、64 ビットと 32 ビットの別個のバージョンがあり、それぞれ Microsoft Office の 64 ビットおよび 32 ビットのエディションによって使用されます。  詳細については、「[Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
## Office ソリューションのアセンブリ  
 Visual Studio の Office 開発ツールを使用して Office プロジェクトを作成した場合、記述したコードは最終的にアセンブリにコンパイルされます。  このアセンブリは、通常、共有サーバーまたはクライアント コンピューター上のディレクトリに配置されます。  
  
 Office ソリューションのアセンブリは Office アプリケーションによって読み込まれます。  アセンブリが読み込まれると、アセンブリ内のコードがアプリケーションで発生するイベント \(ユーザーがメニュー項目をクリックした場合など\) に応答できます。  アセンブリ内のコードでは、オブジェクト モデルを呼び出してアプリケーションの自動化や拡張を行うこともでき、さらに [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] のクラスも使用できます。 詳細については、「[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)」と「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。  
  
 Office ソリューションでは、配置マニフェストとアプリケーション マニフェストを使用してアセンブリを特定します。  これらのマニフェストには、アセンブリの名前、バージョン、および場所に関する情報が含まれているので、アプリケーションでは正しいアセンブリの検索、リンク、および実行ができます。  詳細については、「[Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)」を参照してください。  
  
 ドキュメント レベルのプロジェクトには、アセンブリに加え、ドキュメントも含まれています。  ドキュメントは、アプリケーションのフロント エンドとして機能し、ユーザーはすべての操作をドキュメント上で行います。  各ドキュメントは、メイン プロジェクト アセンブリを 1 つしか関連付けることができませんが、複数のドキュメントが同じアセンブリをポイントすることは可能です。  
  
 ドキュメント レベルのプロジェクトのアセンブリは、ドキュメントに埋め込まれるわけではなく、別の場所に格納されていて、ドキュメントのアプリケーション マニフェストによって識別されます。  
  
## アセンブリのセキュリティに関する考慮事項  
 Office ソリューションをコンピューターで実行する場合、ソリューションに使用されるアセンブリは信頼して実行できる必要があります。  セキュリティの詳細については、「[Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)」を参照してください。  
  
 既定では、プロジェクトの出力フォルダーにあるソリューション アセンブリおよび参照アセンブリは、プロジェクトをビルドするときに開発用コンピューターで信頼して実行できます。  詳細については、「[Office ソリューションのビルド](../vsto/building-office-solutions.md)」を参照してください。  
  
 セキュリティ上の理由により、プロジェクトは、共有の場所に配置するのではなく、ローカル コンピューター上に作成することをお勧めします。  詳細については、「[Office ソリューションの共同開発](../vsto/collaborative-development-of-office-solutions.md)」を参照してください。  
  
## 参照アセンブリ  
 アセンブリは、プロジェクトの参照にリストされている他のアセンブリを参照できます。  ただし、ドキュメント レベルのプロジェクト アセンブリが別のドキュメント レベルのプロジェクト アセンブリを参照することはできません。  
  
## 参照  
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)   
 [異なるバージョンの Microsoft Office でのソリューションの実行](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [方法 : Office ソリューションの構成情報を設定する](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Visual Studio 内での Office 機能の使用](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office プログラミングの共通タスク](../vsto/common-tasks-in-office-programming.md)   
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [Visual Studio の Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  