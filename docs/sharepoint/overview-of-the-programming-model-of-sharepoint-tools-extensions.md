---
title: ツールの拡張機能を SharePoint のプログラミング モデルの概要 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7882439d6c25cf57a435e4bbe046b2121c3e0405
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119511"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>ツールの拡張機能を SharePoint のプログラミング モデルの概要
  Visual Studio で SharePoint ツールの拡張機能を作成する場合、SharePoint ツールによって公開される 1 つ以上の機能拡張インターフェイスを実装することから始めます。 ほとんどの場合、SharePoint ツールによって提供される他の型も使用して、拡張機能で機能を実装します。 一部のシナリオでは、Visual Studio および SharePoint によって提供される他のオブジェクト モデルに含まれる型も使用します。 これらのオブジェクト モデルのそれぞれの目的を理解し、それぞれ他の SharePoint ツールの拡張機能の作成に使用する方法を理解する必要があります。  
  
## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>機能拡張インターフェイスを実装することによって、SharePoint ツールを拡張します。
 Visual Studio は、.NET Framework 4 の Managed Extensibility Framework (MEF) を使用して SharePoint ツールの機能拡張モデルを提供します。 MEF は、アプリケーションが機能拡張ポイントを公開したり、実行時に拡張機能を検出し、読み込んだりできるようにする (System.ComponentModel.Composition アセンブリで実装される) API です。 MEF の詳細については、次を参照してください。 [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index)します。  
  
 SharePoint ツールを拡張するには、Visual Studio によって公開される 1 つ以上の機能拡張インターフェイスを実装します。 <xref:System.ComponentModel.Composition.ExportAttribute>、および必要に応じて SharePoint ツール固有のその他の属性をインターフェイスの実装に適用する必要もあります。 次の表に、SharePoint ツールを拡張するために実装できるインターフェイスを示します。  
  
|Interface|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|このインターフェイスは、新しい種類の SharePoint プロジェクト項目を定義する際に実装します。 例については、次を参照してください。[方法: SharePoint プロジェクト項目の種類定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)します。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|このインターフェイスは、Visual Studio に既にインストールされている SharePoint プロジェクト項目の種類を拡張する場合に実装します。 例については、次を参照してください。[方法: SharePoint プロジェクト項目の拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)です。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|このインターフェイスは、SharePoint プロジェクトを拡張する場合に実装します。 例については、次を参照してください。[方法: SharePoint プロジェクト拡張機能作成](../sharepoint/how-to-create-a-sharepoint-project-extension.md)です。|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|SharePoint プロジェクト項目を配置または取り消すときに実行できる新しい配置手順を定義するには、このインターフェイスを実装します。 例については、次を参照してください。[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|既存のノードを拡張するには、このインターフェイスを実装、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウ。 例については、次を参照してください。[方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)します。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|ノードの下の新しい型を定義するには、このインターフェイスを実装、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウ。 例については、次を参照してください。[方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)します。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|カスタムのフィーチャー検証規則を定義するには、このインターフェイスを実装します。 例については、次を参照してください。[方法: SharePoint ソリューションの検証規則を使用したカスタムのフィーチャーとパッケージの作成](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|カスタムのパッケージ検証規則を定義するには、このインターフェイスを実装します。 例については、次を参照してください。[方法: SharePoint ソリューションの検証規則を使用したカスタムのフィーチャーとパッケージの作成](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。|  
  
 SharePoint ツールの拡張機能を実装したら、拡張機能アセンブリを Visual Studio 拡張機能 (VSIX) のパッケージに配置し、Visual Studio が拡張機能を検出し、読み込むことができるようにする必要があります。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>SharePoint ツール拡張機能で使用するオブジェクト モデルを理解します。
 SharePoint ツールの拡張機能を作成するときに使用できるいくつかのオブジェクト モデルを次に示します。  
  
-   *SharePoint ツールのオブジェクト モデル*します。 このオブジェクト モデルには、SharePoint ツールの拡張機能を作成するために実装する機能拡張インターフェイスと、その他の関連する型が用意されています。  
  
-   *Visual Studio オートメーションとの統合オブジェクト モデル*します。 これらのオブジェクト モデルを使用して、SharePoint ツールのオブジェクト モデルの範囲を超える Visual Studio の機能にアクセスします。  
  
    > [!NOTE]  
    >  SharePoint ツールのオブジェクト モデルに存在するいくつかのオブジェクトは、SharePoint プロジェクト サービスを使用して、Visual Studio のオートメーション オブジェクト モデルおよび Visual Studio の統合オブジェクト モデルのオブジェクトに変換できます。それとは逆方向の変換も可能です。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間で変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)します。  
  
-   *SharePoint サーバーとクライアント オブジェクト モデル*します。 これらのオブジェクト モデルを使用して、SharePoint サイトに変更を加えたり、SharePoint ツールの拡張機能のコンテキストから SharePoint サイトのデータを取得したりします。  
  
### <a name="sharepoint-tools-object-model"></a>SharePoint ツールのオブジェクト モデル
 SharePoint ツールの各拡張機能では、SharePoint ツールのオブジェクト モデルの型を使用して、拡張機能の主要な動作と機能が定義されます。 次の表では、それらを含むアセンブリをこのオブジェクト モデルに含まれている名前空間について説明します。

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll    
|名前空間|説明|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint>|SharePoint プロジェクト システムを拡張および自動化するために使用する型があります。 たとえば、組み込みの SharePoint プロジェクトやプロジェクト項目を拡張できるほか、独自のプロジェクト項目を作成することもできます。 詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張](../sharepoint/extending-the-sharepoint-project-system.md)します。|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|独自の配置手順や配置構成の作成など、SharePoint プロジェクトの配置プロセスを拡張するために使用する型があります。 詳細については、次を参照してください。 [SharePoint の拡張のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)します。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|使用の下のノードを拡張する型が含まれています、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウ、またはノードの新しい型を定義します。 詳細については、次を参照してください。[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。|  
|<xref:Microsoft.VisualStudio.SharePoint.Features>|SharePoint プロジェクトのフィーチャーの定義にアクセスするために使用する型があります。|  
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|SharePoint ソリューションのパッケージ定義にアクセスするために使用する型があります。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|SharePoint プロジェクトの機能およびパッケージ検証動作をカスタマイズするために使用する型があります。 詳細については、次を参照してください。[方法: SharePoint ソリューションの検証規則を使用したカスタムのフィーチャーとパッケージの作成](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。| 

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll
|名前空間|説明|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|カスタムの作成に使用できる型を含む*SharePoint コマンド*します。 SharePoint コマンドは、SharePoint のサーバー オブジェクト モデルに対する呼び出しを SharePoint ツールの拡張機能から行うメソッドです。 詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll
|名前空間|説明|  
|-|-| 
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|組み込みに関する情報の取得に使用できる型を含む**サーバー エクスプ ローラー**リスト、フィールド、またはコンテンツの種類を表すノードなどの SharePoint サイト上の個々 のコンポーネントを表すノード。 詳細については、次を参照してください。[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。|  
  
### <a name="visual-studio-automation-object-model"></a>Visual Studio オートメーション オブジェクト モデル
 Visual Studio のオートメーション オブジェクト モデルには、Visual Studio のプロジェクトおよび IDE を自動化するために使用できる API が用意されています。 SharePoint プロジェクトに限定されないプロジェクト関連のタスクや、Visual Studio の全般的なオートメーション タスクを実行するには、Visual Studio のオブジェクト モデルを使用します。 このオブジェクト モデルは、以前から Visual Studio のアドインやマクロで使用されていましたが、SharePoint ツールの拡張機能で使用することもできます。  
  
 Visual Studio オートメーション オブジェクト モデルの主要部分が定義されている、 *EnvDTE.dll*アセンブリ。 *EnvDTE\\<version>.dll*アセンブリは、Visual Studio の特定のバージョンで導入された追加の機能を提供します。 これらのアセンブリは、Visual Studio に属しています。  
  
 オートメーション オブジェクト モデルの詳細については、次を参照してください。 [Visual Studio SDK リファレンス](../extensibility/visual-studio-sdk-reference.md)します。  
  
### <a name="visual-studio-integration-object-model"></a>Visual Studio の統合オブジェクト モデル
 統合オブジェクト モデルを作成して、Visual Studio に機能を追加するために使用できる Api を提供する、 *VSPackage*します。 VSPackage は、カスタム機能 (ツール ウィンドウ、エディター、デザイナー、サービス、プロジェクトなど) を提供することによって Visual Studio IDE を拡張するモジュールです。  
  
 組み込みの SharePoint ツールと組み合わせて使用する新しい Visual Studio 機能を追加するには、統合オブジェクト モデルを使用します。 たとえば、SharePoint サイトのカスタム動作を表すカスタム SharePoint プロジェクト項目を作成する場合、そのカスタム動作のデザイナーを実装する VSPackage を作成することもできます。 カスタム動作を表すプロジェクト項目にショートカット メニュー項目を追加して、カスタム アクションをデザイナーを関連付けることができます**ソリューション エクスプ ローラー**します。 そのショートカット メニューを開き、デザイナーを開くことができます (カスタム動作プロジェクト項目を右クリックしてまたは選択するかを選択し、 **shift キーを押し**+**F10**キー) しを選択**オープン**します。  
  
 このオブジェクト モデルは、Visual Studio SDK に付属の一連のアセンブリで定義されています。 このオブジェクト モデルでは、メインのアセンブリのものが*Microsoft.VisualStudio.Shell.11.0.dll*、 *Microsoft.VisualStudio.Shell.Interop.dll*、および*Microsoft.visualstudio.ole.interop.dll が含まれます*します。  
  
 統合オブジェクト モデルの詳細については、次を参照してください。[オートメーション モデルの概要](/visualstudio/extensibility/internals/automation-model-overview)と[Visual Studio SDK リファレンス](/visualstudio/extensibility/visual-studio-sdk-reference)します。  
  
### <a name="sharepoint-object-models"></a>SharePoint オブジェクト モデル
 SharePoint ツールの拡張機能から SharePoint の API を使用して、SharePoint サイトに変更を加えたり、SharePoint サイトからデータを取得したりできます。 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] および [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] には、オブジェクト モデルが 2 種類あります。サーバー オブジェクト モデルとクライアント オブジェクト モデルです。  
  
 どちらのオブジェクト モデルの API も SharePoint ツールの拡張機能から使用できます。ただし、SharePoint ツールの拡張機能からこれらのオブジェクト モデルを使用する場合、それぞれ長所と短所があります。 詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。  
  
|オブジェクト モデル|説明|  
|------------------|-----------------|  
|サーバー オブジェクト モデル|サーバー オブジェクト モデルを使用すると、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] および [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] が公開しているすべての機能をプログラムから使用することができます。 このオブジェクト モデルは、SharePoint サーバー上で動作する SharePoint ソリューションから使用することを前提に設計されています。 このオブジェクト モデルの大部分がで定義されている、 *Microsoft.SharePoint.dll*アセンブリ。 サーバー オブジェクト モデルの詳細については、次を参照してください。 [SharePoint Foundation サーバー側オブジェクト モデルを使用して](http://go.microsoft.com/fwlink/?LinkId=177796)します。|  
|クライアント オブジェクト モデル|クライアント オブジェクト モデルは、リモート クライアントまたはリモート サーバーの SharePoint データとの相互運用に使用できるサーバー オブジェクト モデルのサブセットです。 一般的なタスクに必要なラウンド トリップの回数を最小限に抑えるようにデザインされています。 クライアント オブジェクト モデルの大部分がで定義されている、 *Microsoft.SharePoint.Client.dll*と*Microsoft.SharePoint.Client.Runtime.dll*アセンブリ。 クライアント オブジェクト モデルの詳細については、次を参照してください。[マネージ クライアント オブジェクト モデル](http://go.microsoft.com/fwlink/?LinkId=177797)します。|  
  
## <a name="see-also"></a>関連項目
 [Visual Studio の SharePoint ツールを拡張します。](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [SharePoint プロジェクト サービスを使用します。](../sharepoint/using-the-sharepoint-project-service.md)  
  
