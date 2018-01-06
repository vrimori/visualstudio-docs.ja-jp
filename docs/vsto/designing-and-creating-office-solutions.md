---
title: "設計と、Office ソリューションの作成 |Microsoft ドキュメント"
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
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
ms.assetid: 53c32c61-3d3a-4427-a5a7-f9c2c8f1de02
caps.latest.revision: "103"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8b7322faa797ea9ce51af0cd716ffb6536f062ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="designing-and-creating-office-solutions"></a>Office ソリューションのデザインと作成
  Visual Studio には、さまざまな種類の Office ソリューションの作成に使用できるプロジェクト テンプレートが用意されています。 ここでは、プロジェクト テンプレートについて説明し、Office プロジェクトを作成するためのガイダンスを示します。 プロジェクトを作成した後に、コードやユーザー インターフェイスのカスタマイズを実装する方法については、次を参照してください。 [Office ソリューションの開発](../vsto/developing-office-solutions.md)です。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="creating-office-projects"></a>Office プロジェクトの作成  
 開始する前に、要件を決定し、最適なソリューションの種類を探します。 たとえば、アプリケーションを使用するたびに作成した Office ソリューションを実行する必要がある場合は、VSTO アドインが最適です。 コードが 1 つのドキュメントと緊密に統合されている場合は、ドキュメント レベルのカスタマイズを作成します。 これらのプロジェクト タイプは、Visual Studio のプロジェクト テンプレートとして利用できます。 Visual Studio に含まれる Office プロジェクト テンプレートの詳細については、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)です。 Office プロジェクトを作成する方法の詳細については、次を参照してください。[する方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
 Office プロジェクトには、Visual Studio の他の種類のプロジェクトとは異なる機能とプロジェクト項目があります。 たとえば、ドキュメント レベルのプロジェクトを作成した場合は、プロジェクト内の文書またはブックを Visual Studio 内部で開いて編集できます。 詳細については、次を参照してください。 [Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)です。  
  
## <a name="choosing-a-net-framework-version"></a>.NET Framework のバージョンの選択  
 要件に最適なプロジェクトの種類を選択した後に、開発工程で使用する .NET Framework のバージョンを選択できます。 Office プロジェクトでは、次のバージョンの .NET Framework を対象にすることができます。  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 ソリューションを実行するエンド ユーザーのコンピューターには、プロジェクト用に選択した .NET Framework のバージョンが必要です。 たとえば、プロジェクトが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象としている場合、エンド ユーザーのコンピューターには [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] が必要です。 この例では、エンド ユーザーのコンピューターに .NET Framework 3.5 しかインストールされていない場合、ソリューションは実行されません。  
  
 .NET Framework 3.5 を対象とする VSTO アドイン プロジェクトを移行する場合、インストールした Office のバージョンに応じて、Visual Studio によってプロジェクトのターゲット フレームワークが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更されます。  
  
 ただし、プロジェクトで特定の機能を使用している場合は、Visual Studio によるターゲット フレームワークの変更後に、プロジェクトのコードの一部を変更することが必要になる場合があります。 ターゲット フレームワークを変更する方法の詳細については、次を参照してください。[する方法: .NET Framework のバージョンを対象に](../ide/how-to-target-a-version-of-the-dotnet-framework.md)です。 プロジェクトのために必要な場合があります変更の詳細については、次を参照してください。 [Office ソリューションの移行、.NET Framework 4 以降](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)です。  
  
 Visual Studio プロジェクトの対象 .NET Framework の変更、ソリューションを配置する ClickOnce を使用している場合を選択することも、対応する、.NET Framework のバージョンの確認、**の前提条件** ダイアログ ボックス。 プロジェクトのターゲット フレームワークを変更しても、この選択内容は自動的には変わりません。 詳細については、次を参照してください。[する方法: インストールの前提条件エンドユーザーのコンピューターに Office ソリューションを実行する](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)です。  
  
> [!NOTE]  
>  .NET Framework 3.5 以前を [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] を使用して作成した Office プロジェクトの対象にすることはできません。 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] を使用して作成した Office プロジェクトには、[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] で導入された機能が必要です。  
  
### <a name="understanding-when-the-office-pias-are-required-on-end-user-computers"></a>エンド ユーザーのコンピューターで Office PIA が必要な場合について  
 既定では、Office プライマリ相互運用機能アセンブリ (Pia) する必要はありませんするエンドユーザーのコンピューターにインストールされている場合、**相互運用機能型の埋め込み**プロジェクト内の各 Office PIA 参照のプロパティに設定されて**True**、既定値です。 この場合、プロジェクトをビルドすると、ソリューションが使用する PIA 型の型情報がソリューション アセンブリに埋め込まれます。 実行時に、埋め込み型情報は、Office アプリケーションの COM ベース オブジェクト モデルへの呼び出しを Pia の代わりに使用されます。 ソリューションに Pia の型を埋め込む方法の詳細については、次を参照してください。[型の等価性と埋め込まれた相互運用機能型](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)です。  
  
 場合、**相互運用機能型の埋め込み**プロジェクト内の各 Office PIA 参照のプロパティに設定されて**False**、Office Pia をインストールして、各エンドユーザーのコンピューターのグローバル アセンブリ キャッシュに登録する必要がありますをソリューションを実行します。 ほとんどの場合、PIA は既定で Office と共にインストールされますが、ソリューションの必須コンポーネントとして再頒布可能な PIA を含めることもできます。 詳細については、次を参照してください。[展開用の Office ソリューションの必須コンポーネント](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e)です。  
  
### <a name="understanding-the-client-profile"></a>Client Profile について  
 .NET Framework Client Profile は、完全な .NET Framework のサブセットです。 .NET Framework のクライアント機能のみを使用し、Office ソリューションをできる限り迅速に配置する必要がある場合は、.NET Framework Client Profile を対象にすることができます。 詳細については、「[.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)」を参照してください。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とする Office プロジェクトを作成するときに、既定で [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] が対象となります。 完全な [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 用に開発する場合は、プロジェクトを作成した後でこのオプションを設定する必要があります。 詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。  
  
## <a name="creating-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Microsoft Office 64 ビット エディション用のソリューションの作成  
 Microsoft Office には、64 ビットと 32 ビットのエディションがあります。 いずれかのエディションで実行できる Office ソリューションを作成するプロジェクトのプラットフォーム ターゲット設定に設定する必要があります**Any CPU**です。 これは、Office プロジェクトの既定値です。 詳細については、次を参照してください。 [Office ソリューションのビルド](../vsto/building-office-solutions.md)です。  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、64 ビットと 32 ビットの別個のバージョンがあり、それぞれ Microsoft Office の 64 ビットおよび 32 ビットのエディションによって使用されます。 詳細については、「 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
## <a name="assemblies-in-office-solutions"></a>Office ソリューションのアセンブリ  
 Visual Studio の Office 開発ツールを使用して Office プロジェクトを作成した場合、記述したコードは最終的にアセンブリにコンパイルされます。 このアセンブリは、通常、共有サーバーまたはクライアント コンピューター上のディレクトリに配置されます。  
  
 Office ソリューションのアセンブリは Office アプリケーションによって読み込まれます。 アセンブリが読み込まれると、アセンブリ内のコードがアプリケーションで発生するイベント (ユーザーがメニュー項目をクリックした場合など) に応答できます。 アセンブリ内のコードでは、オブジェクト モデルを呼び出してアプリケーションの自動化や拡張を行うこともでき、さらに [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] のクラスも使用できます。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)と[アーキテクチャの VSTO アドイン](../vsto/architecture-of-vsto-add-ins.md)です。  
  
 Office ソリューションでは、配置マニフェストとアプリケーション マニフェストを使用してアセンブリを特定します。 これらのマニフェストには、アセンブリの名前、バージョン、および場所に関する情報が含まれているので、アプリケーションでは正しいアセンブリの検索、リンク、および実行ができます。 詳細については、「 [Application and Deployment Manifests in Office Solutions](../vsto/application-and-deployment-manifests-in-office-solutions.md)」を参照してください。  
  
 ドキュメント レベルのプロジェクトには、アセンブリに加え、ドキュメントも含まれています。 ドキュメントは、アプリケーションのフロント エンドとして機能し、ユーザーはすべての操作をドキュメント上で行います。 各ドキュメントは、メイン プロジェクト アセンブリを 1 つしか関連付けることができませんが、複数のドキュメントが同じアセンブリをポイントすることは可能です。  
  
 ドキュメント レベルのプロジェクトのアセンブリは、ドキュメントに埋め込まれるわけではなく、別の場所に格納されていて、ドキュメントのアプリケーション マニフェストによって識別されます。  
  
## <a name="security-considerations-for-assemblies"></a>アセンブリのセキュリティに関する考慮事項  
 Office ソリューションをコンピューターで実行する場合、ソリューションに使用されるアセンブリは信頼して実行できる必要があります。 セキュリティの詳細については、次を参照してください。 [Office ソリューションのセキュリティで保護する](../vsto/securing-office-solutions.md)です。  
  
 既定では、プロジェクトの出力フォルダーにあるソリューション アセンブリおよび参照アセンブリは、プロジェクトをビルドするときに開発用コンピューターで信頼して実行できます。 詳細については、次を参照してください。 [Office ソリューションのビルド](../vsto/building-office-solutions.md)です。  
  
 セキュリティ上の理由により、プロジェクトは、共有の場所に配置するのではなく、ローカル コンピューター上に作成することをお勧めします。 詳細については、次を参照してください。 [Office ソリューションの共同開発](../vsto/collaborative-development-of-office-solutions.md)です。  
  
## <a name="referenced-assemblies"></a>参照アセンブリ  
 アセンブリは、プロジェクトの参照にリストされている他のアセンブリを参照できます。 ただし、ドキュメント レベルのプロジェクト アセンブリが別のドキュメント レベルのプロジェクト アセンブリを参照することはできません。  
  
## <a name="see-also"></a>参照  
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio 環境における office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)   
 [異なるバージョンの Microsoft Office でソリューションを実行します。](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [アプリケーションおよび Office ソリューションの配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [方法: Office ソリューションの構成情報を設定します](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Visual Studio 内での Office 機能を使用します。](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office プログラミングの共通タスク](../vsto/common-tasks-in-office-programming.md)   
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [Visual Studio の Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  