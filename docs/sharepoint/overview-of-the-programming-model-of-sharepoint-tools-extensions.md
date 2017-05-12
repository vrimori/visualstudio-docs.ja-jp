---
title: "Overview of the Programming Model of SharePoint Tools Extensions"
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
  - "Visual Studio, extending tools"
  - "SharePoint development in Visual Studio, extensibility object models"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Overview of the Programming Model of SharePoint Tools Extensions
  Visual Studio で SharePoint ツールの拡張機能を作成する場合、SharePoint ツールによって公開される 1 つ以上の機能拡張インターフェイスを実装することから始めます。  ほとんどの場合、SharePoint ツールによって提供される他の型も使用して、拡張機能で機能を実装します。  一部のシナリオでは、Visual Studio および SharePoint によって提供される他のオブジェクト モデルに含まれる型も使用します。  これらの各オブジェクト モデルの用途と、これらを組み合わせて使用して SharePoint ツールの拡張機能を作成する方法を理解する必要があります。  
  
## 機能拡張インターフェイスの実装による SharePoint ツールの拡張  
 Visual Studio は、.NET Framework 4 の Managed Extensibility Framework \(MEF\) を使用して SharePoint ツールの機能拡張モデルを提供します。  MEF は、アプリケーションが機能拡張ポイントを公開したり、実行時に拡張機能を検出し、読み込んだりできるようにする \(System.ComponentModel.Composition アセンブリで実装される\) API です。  MEF の詳細については、「[Managed Extensibility Framework &#40;MEF&#41;](../Topic/Managed%20Extensibility%20Framework%20(MEF).md)」を参照してださい。  
  
 SharePoint ツールを拡張するには、Visual Studio によって公開される 1 つ以上の機能拡張インターフェイスを実装します。  <xref:System.ComponentModel.Composition.ExportAttribute>、および必要に応じて SharePoint ツール固有のその他の属性をインターフェイスの実装に適用する必要もあります。  次の表に、SharePoint ツールを拡張するために実装できるインターフェイスを示します。  
  
|インターフェイス|説明|  
|--------------|--------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|このインターフェイスは、新しい種類の SharePoint プロジェクト項目を定義する際に実装します。  例については、「[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|このインターフェイスは、Visual Studio に既にインストールされている SharePoint プロジェクト項目の種類を拡張する場合に実装します。  例については、「[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|このインターフェイスは、SharePoint プロジェクトを拡張する場合に実装します。  例については、「[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|SharePoint プロジェクト項目を配置または取り消すときに実行できる新しい配置手順を定義するには、このインターフェイスを実装します。  例については、「[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|**\[サーバー エクスプローラー\]** ウィンドウの **\[SharePoint 接続\]** ノードの下の既存のノードを拡張するには、このインターフェイスを実装します。  例については、「[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|**\[サーバー エクスプローラー\]** ウィンドウの **\[SharePoint 接続\]** ノードの下の新しい型のノードを拡張するには、このインターフェイスを実装します。  例については、「[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|カスタムのフィーチャー検証規則を定義するには、このインターフェイスを実装します。  例については、「[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|カスタムのパッケージ検証規則を定義するには、このインターフェイスを実装します。  例については、「[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)」を参照してください。|  
  
 SharePoint ツールの拡張機能を実装したら、拡張機能アセンブリを Visual Studio 拡張機能 \(VSIX\) のパッケージに配置し、Visual Studio が拡張機能を検出し、読み込むことができるようにする必要があります。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## SharePoint ツールの拡張機能で使用するオブジェクト モデルについて  
 SharePoint ツールの拡張機能を作成するときに使用できるいくつかのオブジェクト モデルを次に示します。  
  
-   *SharePoint ツールのオブジェクト モデル*。  このオブジェクト モデルには、SharePoint ツールの拡張機能を作成するために実装する機能拡張インターフェイスと、その他の関連する型が用意されています。  
  
-   *Visual Studio のオートメーション オブジェクト モデルと Visual Studio の統合オブジェクト モデル*。  これらのオブジェクト モデルを使用して、SharePoint ツールのオブジェクト モデルの範囲を超える Visual Studio の機能にアクセスします。  
  
    > [!NOTE]  
    >  SharePoint ツールのオブジェクト モデルに存在するいくつかのオブジェクトは、SharePoint プロジェクト サービスを使用して、Visual Studio のオートメーション オブジェクト モデルおよび Visual Studio の統合オブジェクト モデルのオブジェクトに変換できます。それとは逆方向の変換も可能です。  詳細については、「[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)」を参照してください。  
  
-   *SharePoint サーバー オブジェクト モデルと SharePoint クライアント オブジェクト モデル*。  これらのオブジェクト モデルを使用して、SharePoint サイトに変更を加えたり、SharePoint ツールの拡張機能のコンテキストから SharePoint サイトのデータを取得したりします。  
  
### SharePoint ツールのオブジェクト モデル  
 SharePoint ツールの各拡張機能では、SharePoint ツールのオブジェクト モデルの型を使用して、拡張機能の主要な動作と機能が定義されます。  以下の表に、このオブジェクト モデルに含まれる名前空間を示します。  
  
|Assembly|名前空間|説明|  
|--------------|----------|--------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|SharePoint プロジェクト システムを拡張および自動化するために使用する型があります。  たとえば、組み込みの SharePoint プロジェクトやプロジェクト項目を拡張できるほか、独自のプロジェクト項目を作成することもできます。  詳細については、「[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)」を参照してください。|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|独自の配置手順や配置構成の作成など、SharePoint プロジェクトの配置プロセスを拡張するために使用する型があります。  詳細については、「[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)」を参照してください。|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|**\[サーバー エクスプローラー\]** ウィンドウの **\[SharePoint 接続\]** ノードの下のノードを拡張したり、新しい型のノードを定義したりするために使用する型があります。  詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|SharePoint プロジェクトの機能の定義にアクセスするために使用する型があります。|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|SharePoint ソリューションのパッケージ定義にアクセスするために使用する型があります。|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|SharePoint プロジェクトの機能およびパッケージ検証動作をカスタマイズするために使用する型があります。  詳細については、「[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)」を参照してください。|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|カスタム *SharePoint コマンド*の作成に使用できる型があります。  SharePoint コマンドは、SharePoint のサーバー オブジェクト モデルに対する呼び出しを SharePoint ツールの拡張機能から行うメソッドです。  詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|リスト、フィールド、コンテンツ タイプを表すノードなど、SharePoint サイトの個々のコンポーネントを表す、組み込みの**サーバー エクスプローラー** ノードに関する情報を取得するために使用する型があります。  詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。|  
  
### Visual Studio オートメーション オブジェクト モデル  
 Visual Studio のオートメーション オブジェクト モデルには、Visual Studio のプロジェクトおよび IDE を自動化するために使用できる API が用意されています。  SharePoint プロジェクトに限定されないプロジェクト関連のタスクや、Visual Studio の全般的なオートメーション タスクを実行するには、Visual Studio のオブジェクト モデルを使用します。  このオブジェクト モデルは、以前から Visual Studio のアドインやマクロで使用されていましたが、SharePoint ツールの拡張機能で使用することもできます。  
  
 Visual Studio のオートメーション オブジェクト モデルの核となる部分は EnvDTE.dll アセンブリに定義されています。  EnvDTE80.dll、EnvDTE90.dll、EnvDTE100.dll、および EnvDTE110.dll のアセンブリは、Visual Studio 2005、Visual Studio 2008、Visual Studio 2010、および [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] で導入された追加機能をそれぞれ提供します。  これらのアセンブリは、Visual Studio に属しています。  
  
 オートメーション オブジェクト モデルの詳細については、「[Extending the Visual Studio Environment](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)」および「[Automation and Extensibility Reference](../Topic/Automation%20and%20Extensibility%20Reference.md)」を参照してください。  
  
### Visual Studio の統合オブジェクト モデル  
 統合オブジェクト モデルには、*VSPackage* の作成によって Visual Studio に機能を追加することのできる API が用意されています。  VSPackage は、カスタム機能 \(ツール ウィンドウ、エディター、デザイナー、サービス、プロジェクトなど\) を提供することによって Visual Studio IDE を拡張するモジュールです。  
  
 組み込みの SharePoint ツールと組み合わせて使用する新しい Visual Studio 機能を追加するには、統合オブジェクト モデルを使用します。  たとえば、SharePoint サイトのカスタム動作を表すカスタム SharePoint プロジェクト項目を作成する場合、そのカスタム動作のデザイナーを実装する VSPackage を作成することもできます。  **\[ソリューション エクスプローラー\]** のカスタム動作を表すプロジェクト項目にショートカット メニュー項目を追加すると、カスタム動作とデザイナーを関連付けることができます。  ショートカット メニューを開いてから \(カスタム動作プロジェクト項目を右クリックするか、カスタム動作プロジェクト項目を選択し、Shift キーを押しながら F10 キーを押すことで開きます\)、**\[開く\]** をクリックすることにより、デザイナーを開くことができます。  
  
 このオブジェクト モデルは、Visual Studio SDK に付属の一連のアセンブリで定義されています。  このオブジェクト モデルでは、メインのアセンブリの一部には Microsoft.VisualStudio.Shell.11.0.dll、Microsoft.VisualStudio.Shell.Interop.dll、および Microsoft.VisualStudio.OLE.Interop.dll が含まれます。  
  
 統合オブジェクト モデルの詳細については、「[Visual Studio 機能拡張アーキテクチャ](/visual-cpp/misc/visual-studio-extensibility-architecture)」および「[Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)」を参照してください。  
  
### SharePoint のオブジェクト モデル  
 SharePoint ツールの拡張機能から SharePoint の API を使用して、SharePoint サイトに変更を加えたり、SharePoint サイトからデータを取得したりできます。  [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] および [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] には、オブジェクト モデルが 2 種類あります。サーバー オブジェクト モデルとクライアント オブジェクト モデルです。  
  
 どちらのオブジェクト モデルの API も SharePoint ツールの拡張機能から使用できます。ただし、SharePoint ツールの拡張機能からこれらのオブジェクト モデルを使用する場合、それぞれ長所と短所があります。  詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。  
  
|オブジェクト モデル|説明|  
|----------------|--------|  
|サーバー オブジェクト モデル|サーバー オブジェクト モデルを使用すると、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] および [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] が公開しているすべての機能をプログラムから使用することができます。  このオブジェクト モデルは、SharePoint サーバー上で動作する SharePoint ソリューションから使用することを前提に設計されています。  このオブジェクト モデルの大部分は、Microsoft.SharePoint.dll アセンブリで定義されています。  サーバー オブジェクト モデルの詳細については、「[SharePoint Foundation サーバー側のオブジェクト モデルを使用する](http://go.microsoft.com/fwlink/?LinkId=177796)」を参照してください。|  
|クライアント オブジェクト モデル|クライアント オブジェクト モデルは、リモート クライアントまたはリモート サーバーの SharePoint データとの相互運用に使用できるサーバー オブジェクト モデルのサブセットです。  一般的なタスクに必要なラウンド トリップの回数を最小限に抑えるようにデザインされています。  クライアント オブジェクト モデルの大部分は、Microsoft.SharePoint.Client.dll および Microsoft.SharePoint.Client.Runtime.dll アセンブリで定義されています。  クライアント オブジェクト モデルの詳細については、「[マネージ クライアント オブジェクト モデル](http://go.microsoft.com/fwlink/?LinkId=177797)」を参照してください。|  
  
## 参照  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)  
  
  