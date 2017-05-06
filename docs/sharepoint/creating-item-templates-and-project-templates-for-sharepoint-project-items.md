---
title: "Creating Item Templates and Project Templates for SharePoint Project Items"
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
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  カスタムの SharePoint プロジェクト項目の種類を定義したら、そのプロジェクト項目を他の開発者が Visual Studio で使用できるように、項目テンプレートまたはプロジェクト テンプレートに関連付けることができます。  テンプレートのウィザードを作成することもできます。  
  
 たとえば、Visual Studio には、SharePoint サイトにフィールドを追加するためのプロジェクト テンプレートまたは項目テンプレートは用意されていません。  フィールドを表す SharePoint プロジェクト項目の種類を定義し、その後、他の開発者がそのフィールド項目を SharePoint プロジェクトに追加するために使用できる項目テンプレートを作成できます。  または開発者がそのフィールド項目を含む新しいSharePointプロジェクトを作成できるように、プロジェクト テンプレートを作成することもできます。いずれの場合も、開発者がテンプレートを使用すると表示されるウィザードを提供できます。  このウィザードで、開発者から情報を収集して新しい項目またはプロジェクトを構成できます。  
  
 項目テンプレートおよびプロジェクト テンプレートは、プロジェクト項目またはプロジェクトを作成するために Visual Studio によって使用されるファイルが含まれる .zip ファイルです。  項目テンプレートおよびプロジェクト テンプレートの基本事項の詳細については、「[Visual Studio でのカスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)」を参照してください。  
  
##  <a name="creatingitemtemplates"></a> 項目テンプレートの作成  
 SharePoint プロジェクト項目の項目テンプレートを作成する場合、いくつかの必ず必要なファイルと、特定の種類のプロジェクト項目によって使用される可能性がある省略可能なファイルがあります。  SharePoint プロジェクト項目の種類を定義し、その項目テンプレートを作成する方法を示すチュートリアルについては、「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)」を参照してください。  
  
 次の表に、SharePoint プロジェクト項目の項目テンプレートを作成するための必須ファイルを示します。  
  
|必須ファイル|説明|  
|------------|--------|  
|.spdata ファイル|このファイルは、プロジェクト項目の内容と既定の動作を指定する XML ファイルです。  このファイルが項目テンプレートに含まれている必要があります。  .spdata ファイルの内容の詳細については、「[SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)」を参照してください。|  
|.vstemplate ファイル。|このファイルは、**\[新しい項目の追加\]** ダイアログ ボックスでテンプレートを表示したり、テンプレートからプロジェクト項目を作成したりするために必要な情報を Visual Studio に提供します。  このファイルが項目テンプレートに含まれている必要があります。  詳細については、「[NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/ja-jp/129d59b5-7f9c-4daf-9832-eaedb3c4c961)」を参照してください。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装する Visual Studio 拡張機能アセンブリ。|このアセンブリは、プロジェクト項目の実行時の動作を定義します。  このアセンブリが、項目テンプレートと共に VSIX パッケージに含まれている必要があります。  詳細については、「[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)」および「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。|  
  
 次の表に、項目テンプレートに含めることができる最も一般的な省略可能なファイルをいくつか示します。  一部の種類のプロジェクト項目では、ここに示されていない他のファイルが必要になる場合があります。  
  
|省略可能なファイル|説明|  
|---------------|--------|  
|Elements.xml|*フィーチャー要素*ファイル。  プロジェクト項目によって作成されるカスタマイズの UI と動作を定義するファイルです。  リスト インスタンス、コンテンツ タイプ、カスタム動作など、カスタマイズの種類によって、このファイルの内容を定義するスキーマも異なります。  詳細については、「[Building Block: Features \(ビルド ブロック: フィーチャー\)](http://go.microsoft.com/fwlink/?LinkID=169183)」および「[Feature Schemas \(フィーチャー スキーマ\)](http://go.microsoft.com/fwlink/?LinkID=169192)」を参照してください。|  
|Schema.xml|リスト定義のスキーマ ファイル。  詳細については、「[Building Block: Lists and Document Libraries \(ビルド ブロック: リストおよびドキュメント ライブラリ\)](http://go.microsoft.com/fwlink/?LinkId=177792)」および「[Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)」を参照してください。|  
|.webpart|*Web パーツ定義*ファイル。  Web パーツのプロパティ設定を記述するファイルです。  詳細については、「[Building Block: Web Parts \(ビルド ブロック: Web パーツ\)](http://go.microsoft.com/fwlink/?LinkId=177791)」を参照してください。|  
|.ascx|ASP.NET UserControl ファイル。  可視 Web パーツの UI を定義するファイルです。|  
|.aspx|ASP.NET ページ ファイル。  アプリケーション ページを定義する XML マークアップを記述するファイルです。|  
|.cs ファイルまたは .vb ファイル|アプリケーション ページ、Web パーツ、ワークフローなど、Visual C\# コードまたは Visual Basic コードからアクセスできるプログラミング モデルがある SharePoint のカスタマイズの動作を定義するコード ファイルです。|  
  
## プロジェクト テンプレートの作成  
 SharePoint プロジェクト テンプレートを作成する場合、いくつかの必ず必要なファイルと、特定の種類のプロジェクトによって使用される可能性がある省略可能なファイルがあります。  通常、SharePoint プロジェクトには少なくとも 1 つの SharePoint プロジェクト項目が含まれます。  ただし、これは必須ではありません。  たとえば、他のプロジェクトで作成された SharePoint ソリューションを配置するためだけの SharePoint プロジェクト テンプレートを定義することもできます。  
  
 SharePoint プロジェクト項目の種類を定義し、そのプロジェクト テンプレートを作成する方法を示すチュートリアルについては、「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 1&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)」を参照してください。  
  
 次の表に、SharePoint プロジェクト テンプレートに含まれている必要があるファイルを示します。  
  
|必須ファイル|説明|  
|------------|--------|  
|.vstemplate ファイル|このファイルは、**\[新しいプロジェクト\]** ダイアログ ボックスでテンプレートを表示したり、テンプレートからプロジェクトを作成したりするために必要な情報を Visual Studio に提供します。  詳細については、「[NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/ja-jp/129d59b5-7f9c-4daf-9832-eaedb3c4c961)」を参照してください。|  
|.csproj ファイルまたは .vbproj ファイル|これはプロジェクト ファイルです。  このファイルは、プロジェクトのコンテンツおよび構成設定を定義します。|  
|Package.package|プロジェクトの配置パッケージを定義するファイルです。  パッケージ デザイナーを使用してプロジェクトのソリューション パッケージをカスタマイズするときに、ソリューション パッケージに関するデータがこのファイルに保存されます。<br /><br /> カスタムの SharePoint プロジェクト テンプレートを作成する場合は、Package.package ファイルの内容を必要最小限にすること、また、プロジェクト テンプレートに関連付ける拡張機能で <xref:Microsoft.VisualStudio.SharePoint.Packages> 名前空間の API を使用してソリューション パッケージを構成することをお勧めします。  これにより、Package.package ファイルの構造を将来変更した場合に、プロジェクト テンプレートへの影響を抑えることができます。  必要最小限の内容にした Package.package ファイルを作成する方法を示す例については、「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 1&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)」を参照してください。<br /><br /> Package.package ファイルを直接変更する場合は、%Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd にあるスキーマを使用して、その内容を検証できます。|  
|Package.Template.xml|プロジェクトから生成される SharePoint ソリューション パッケージ \(.wsp\) のソリューション マニフェスト ファイル \(manifest.xml\) の基礎となるファイルです。  目的のプロジェクトの種類を使用するユーザーには変更できないようにする動作を指定する場合は、このファイルに内容を追加できます。  詳細については、「[Building Block: Solutions \(ビルド ブロック: ソリューション\)](http://go.microsoft.com/fwlink/?LinkId=169186)」および「[ソリューション スキーマ](http://go.microsoft.com/fwlink/?LinkId=177794)」を参照してください。<br /><br /> プロジェクトからソリューション パッケージを作成するときに、Package.package ファイルと Package.Template.xml ファイルの内容がソリューション マニフェスト ファイルにマージされます。  ソリューション パッケージの作成の詳細については、「[How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/ja-jp/b24be45c-e91d-49bb-afb0-7b265404214b)」を参照してください。|  
  
 次の表に、プロジェクト テンプレートに含めることができる省略可能なファイルを示します。  
  
|省略可能なファイル|説明|  
|---------------|--------|  
|SharePoint プロジェクト項目|SharePoint プロジェクト項目の種類を定義する 1 つ以上の .spdata ファイルを含めることができます。  各 .spdata ファイルには、プロジェクト テンプレートと共に VSIX パッケージに含まれる拡張機能アセンブリに、対応する <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 実装がある必要があります。  詳細については、「[項目テンプレートの作成](#creatingitemtemplates)」を参照してください。<br /><br /> 通常、SharePoint プロジェクトには少なくとも 1 つの SharePoint プロジェクト項目が含まれます。  ただし、これは必須ではありません。|  
|*\<フィーチャー名\>*.feature|配置用の複数のプロジェクト項目をグループ化するために使用する SharePoint フィーチャーを定義するファイルです。  フィーチャー デザイナーを使用してプロジェクトのフィーチャーをカスタマイズするときに、フィーチャーに関するデータがこのファイルに保存されます。  プロジェクト項目を別々のフィーチャーにグループ化する場合は、複数の .feature ファイルを含めることができます。<br /><br /> カスタムの SharePoint プロジェクト テンプレートを作成する場合は、各 .feature ファイルの内容を必要最小限にすること、また、プロジェクト テンプレートに関連付ける拡張機能で <xref:Microsoft.VisualStudio.SharePoint.Features> 名前空間の API を使用してフィーチャーを構成することをお勧めします。  これにより、.feature ファイルの構造を将来変更した場合に、プロジェクト テンプレートへの影響を抑えることができます。  必要最小限の内容にした .feature ファイルを作成する方法を示す例については、「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 1&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)」を参照してください。<br /><br /> .feature ファイルを直接変更する場合は、%Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd にあるスキーマを使用して、その内容を検証できます。|  
|*\<フィーチャー名\>*.Template.xml|プロジェクトから生成される各フィーチャーのフィーチャー マニフェスト ファイル \(Feature.xml\) の基礎となるファイルです。  目的のプロジェクトの種類を使用するユーザーには変更できないようにする動作を指定する場合は、このファイルに内容を追加できます。  詳細については、「[Building Block: Features \(ビルド ブロック: フィーチャー\)](http://go.microsoft.com/fwlink/?LinkID=169183)」および「[Feature.xml ファイル](http://go.microsoft.com/fwlink/?LinkID=177795)」を参照してください。<br /><br /> プロジェクトからソリューション パッケージを作成するときに、*\<フィーチャー名\>*.feature ファイルと *\<フィーチャー名\>*.Template.xml ファイルの各組み合わせの内容がフィーチャー マニフェスト ファイルにマージされます。  ソリューション パッケージの作成の詳細については、「[How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/ja-jp/b24be45c-e91d-49bb-afb0-7b265404214b)」を参照してください。|  
  
## 項目テンプレートとプロジェクト テンプレートのウィザードの作成  
 SharePoint プロジェクト項目の種類を定義して、それを項目またはプロジェクト テンプレートに関連付けたら、ウィザードを作成することもできます。  ウィザードは、開発者が項目テンプレートを使用して SharePoint プロジェクト項目をプロジェクトに追加する場合、または開発者がプロジェクト テンプレートを使用して SharePoint プロジェクト項目を含む新しいプロジェクトを作成する場合に表示されます。  開発者から情報を収集する場合、および新しい SharePoint プロジェクト項目を初期化する場合にウィザードを使用できます。  
  
 項目テンプレートおよびプロジェクト テンプレートのウィザードを作成する方法を説明するチュートリアルについては、「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)」および「[チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)」を参照してください。  
  
## 参照  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 1&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Visual Studio でのカスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)  
  
  