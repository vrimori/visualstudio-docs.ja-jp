---
title: "作成する項目テンプレートとプロジェクト テンプレートの SharePoint プロジェクト項目 |Microsoft ドキュメント"
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
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1946d31d1e0f508267300c14551b0a8efff81587
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>SharePoint プロジェクト項目の項目テンプレートとプロジェクト テンプレートの作成
  カスタム SharePoint プロジェクト項目の種類を定義するときにすることができますまたはに関連付けること項目テンプレート プロジェクト テンプレートの他の開発者が Visual Studio でプロジェクト項目を使用できるようにします。 テンプレートのウィザードを作成することもできます。  
  
 たとえば、Visual Studio は、プロジェクト テンプレートや項目テンプレートのフィールドを SharePoint サイトに追加するには含まれません。 フィールドを表す SharePoint プロジェクト項目の種類を定義し、フィールドの項目を SharePoint プロジェクトに追加する他の開発者が使用できる項目テンプレートを作成できます。 または、プロジェクト テンプレートを作成するには、開発者は、フィールドの項目を含む新しい SharePoint プロジェクトを作成できるようにします。 どちらの場合、開発者が、テンプレートを使用するときに表示されるウィザードを指定することもできます。 このウィザードでは、開発者は、新しい項目の追加またはプロジェクトの構成から情報を収集できます。  
  
 項目テンプレートとプロジェクト テンプレートは、Visual Studio によってプロジェクト アイテムやプロジェクトを作成するために使用したファイルを含む .zip ファイルです。 項目テンプレートとプロジェクト テンプレートの基礎の詳細については、次を参照してください。[を作成するプロジェクトと項目テンプレート](/visualstudio/ide/creating-project-and-item-templates)です。  
  
##  <a name="creatingitemtemplates"></a>項目テンプレートを作成します。  
 SharePoint プロジェクト項目の項目テンプレートを作成するときにいくつかは常に、必要なファイルおよびプロジェクト項目の特定の種類によって使用される省略可能なファイルです。 SharePoint プロジェクト項目の種類を定義し、その項目テンプレートを作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)です。  
  
 次の表は、SharePoint プロジェクト項目の項目テンプレートの作成に必要なファイルを一覧表示します。  
  
|必要なファイル|説明|  
|-------------------|-----------------|  
|.Spdata ファイル|これは、内容と、プロジェクト項目の既定の動作を指定する XML ファイルです。 このファイルは、項目テンプレートに含める必要があります。 .Spdata ファイルの内容に関する詳細については、次を参照してください。 [SharePoint プロジェクト項目のスキーマ リファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)です。|  
|.Vstemplate ファイルです。|このファイルには、Visual Studio でテンプレートを表示するために必要な情報、**新しい項目の追加** ダイアログ ボックスと、テンプレートからプロジェクト項目を作成します。 このファイルは、項目テンプレートに含める必要があります。 詳細については、次を参照してください。 [Visual Studio テンプレートのメタデータ ファイル](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)です。|  
|実装する Visual Studio 拡張機能アセンブリ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>インターフェイスです。|このアセンブリでは、プロジェクト項目の実行時の動作を定義します。 このアセンブリは、項目テンプレートを使用して VSIX パッケージに含める必要があります。 詳細については、次を参照してください。[カスタム SharePoint プロジェクト項目の種類を定義する](../sharepoint/defining-custom-sharepoint-project-item-types.md)と[Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。|  
  
 次の表には、一部の項目テンプレートに含めることのできる最も一般的な省略可能なファイルが一覧表示します。 プロジェクト項目の種類によっては、記載されていないその他のファイルを必要があります。  
  
|省略可能なファイル|説明|  
|-------------------|-----------------|  
|Elements.xml|A*フィーチャー要素*ファイル。 このファイルは、プロジェクト項目で作成、カスタマイズの動作と UI を定義します。 各種類のリスト インスタンス、コンテンツの種類、またはカスタムの動作などのカスタマイズでは、このファイルの内容を定義する別のスキーマがします。 詳細については、次を参照してください。[ビルディング ブロック: 機能](http://go.microsoft.com/fwlink/?LinkId=169183)と[機能スキーマ](http://go.microsoft.com/fwlink/?LinkId=169192)です。|  
|Schema.xml|リストの定義のスキーマ ファイルです。 詳細については、次を参照してください。[ビルディング ブロック: リストとドキュメント ライブラリ](http://go.microsoft.com/fwlink/?LinkId=177792)と[Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)です。|  
|.webpart|A *Web パーツ定義*ファイル。 このファイルには、Web パーツのプロパティ設定が含まれています。 詳細については、次を参照してください。[ビルディング ブロック: Web パーツ](http://go.microsoft.com/fwlink/?LinkId=177791)です。|  
|.ascx|ASP.NET ユーザー コントロール ファイルの場合です。 このファイルは、視覚的 Web パーツの UI を定義します。|  
|.aspx|ASP.NET ページ ファイルです。 このファイルには、アプリケーション ページを定義する XML マークアップが含まれています。|  
|.cs または .vb ファイル|これらのコード ファイルでは、Visual c# または Visual Basic コード、アプリケーション ページ、Web パーツ、ワークフローなどからアクセスできるプログラミング モデルが、SharePoint のカスタマイズの動作を定義します。|  
  
## <a name="creating-project-templates"></a>プロジェクト テンプレートを作成します。  
 SharePoint プロジェクト テンプレートを作成するときに特定の種類のプロジェクトで使用される、必須およびオプションのファイルは、常にいくつかのファイルがあります。 通常、SharePoint プロジェクトには、少なくとも 1 つの SharePoint プロジェクト項目が含まれます。 ただし、これは必要ではありません。 たとえば、他のプロジェクトで作成した SharePoint ソリューションの展開にのみ使用するためのものでは、SharePoint プロジェクト テンプレートを定義できます。  
  
 SharePoint プロジェクト項目の種類を定義し、そのプロジェクト テンプレートを作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 1 部に基づくサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)です。  
  
 次の表は、SharePoint プロジェクトのテンプレートに含める必要があるファイルを示します。  
  
|必要なファイル|説明|  
|-------------------|-----------------|  
|.Vstemplate ファイル|このファイルには、Visual Studio でテンプレートを表示するために必要な情報、**新しいプロジェクト** ダイアログ ボックスと、テンプレートからプロジェクトを作成します。 詳細については、次を参照してください。 [Visual Studio テンプレートのメタデータ ファイル](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)です。|  
|Csproj ファイルまたは .vbproj ファイル|これは、プロジェクト ファイルです。 これは、内容と、プロジェクトの構成設定を定義します。|  
|Package.package|このファイルは、プロジェクトの配置パッケージを定義します。 パッケージ デザイナーを使用して、プロジェクトのソリューション パッケージをカスタマイズするときに、Visual Studio は、このファイルにソリューション パッケージに関するデータを格納します。<br /><br /> 最低限必要 Package.package ファイルの内容のみを含めることと、Api を使用して、ソリューション パッケージを構成することをお勧めカスタム SharePoint プロジェクト テンプレートを作成するときに、<xref:Microsoft.VisualStudio.SharePoint.Packages>される拡張機能の名前空間プロジェクト テンプレートと関連付けられています。 これを行う場合、プロジェクト テンプレートが Package.package ファイルの構造に将来の変更から保護されます。 たとえば、Package.package ファイルをコンテンツのみの最小要件を作成する方法については、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 1 部に基づくサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)です。<br /><br /> Package.package ファイルを直接変更する場合は、プログラム ファイル (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd %3 でスキーマを使用して内容を確認できます。|  
|Package.Template.xml|このファイルは、プロジェクトから生成される SharePoint ソリューション パッケージ (.wsp) のソリューション マニフェスト ファイル (manifest.xml) の基礎を提供します。 プロジェクトの種類のユーザーが変更するものではありません一部の動作を指定する場合は、このファイルにコンテンツを追加できます。 詳細については、次を参照してください。[ビルディング ブロック: ソリューション](http://go.microsoft.com/fwlink/?LinkId=169186)と[ソリューション スキーマ](http://go.microsoft.com/fwlink/?LinkId=177794)です。<br /><br /> プロジェクトから、ソリューション パッケージをビルドすると、Visual Studio が、Package.package の内容をマージし、マニフェスト ファイルをソリューションに Package.Template.xml ファイル。 ソリューション パッケージの構築に関する詳細については、次を参照してください。[する方法: SharePoint ソリューション パッケージ (wsp) を作成](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)です。|  
  
 次の表は、プロジェクトのテンプレートに含めることができる省略可能なファイルを示します。  
  
|省略可能なファイル|説明|  
|-------------------|-----------------|  
|SharePoint プロジェクト項目|SharePoint プロジェクト項目の種類を定義する 1 つまたは複数の .spdata ファイルを含めることができます。 .Spdata ファイルごとの対応する必要がありますが<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>プロジェクト テンプレートを使用して VSIX パッケージに含まれている拡張機能アセンブリで実装します。 詳細については、次を参照してください。[項目テンプレートの作成](#creatingitemtemplates)です。<br /><br /> 通常、SharePoint プロジェクトには、少なくとも 1 つの SharePoint プロジェクト項目が含まれます。 ただし、これは必要ではありません。|  
|*featureName*.feature|このファイルは、展開の複数のプロジェクト項目をグループ化に使用される SharePoint 機能を定義します。 フィーチャー デザイナーを使用して、プロジェクトの機能をカスタマイズするときに Visual Studio は、このファイルに、機能に関するデータを格納します。 さまざまな機能にプロジェクト項目をグループ化する場合は、複数の .feature ファイルを含めることができます。<br /><br /> 各 .feature ファイルに、最低限必要なコンテンツのみを含めるしで Api を使用して機能を構成することをお勧めカスタム SharePoint プロジェクト テンプレートを作成するときに、<xref:Microsoft.VisualStudio.SharePoint.Features>名前空間に関連付けられている拡張機能で、プロジェクト テンプレートです。 これを行う場合、プロジェクト テンプレートが .feature ファイルの構造に将来の変更から保護されます。 たとえば、コンテンツのみのために最低限の .feature ファイルを作成する方法については、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 1 部に基づくサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)です。<br /><br /> .Feature ファイルを直接変更する場合は、プログラム ファイル (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd %3 でスキーマを使用して内容を確認できます。|  
|*featureName*です。Template.xml|このファイルは、プロジェクトから生成された各機能に対して、フィーチャー マニフェスト ファイル (Feature.xml) の基礎を提供します。 プロジェクトの種類のユーザーが変更するものではありません一部の動作を指定する場合は、このファイルにコンテンツを追加できます。 詳細については、次を参照してください。[ビルディング ブロック: 機能](http://go.microsoft.com/fwlink/?LinkId=169183)と[Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795)ファイル。<br /><br /> Visual Studio プロジェクトから、ソリューション パッケージをビルドするときの各ペアの内容と結合*featureName*.feature ファイルおよび*featureName*です。フィーチャー マニフェスト ファイルに Template.xml ファイル。 ソリューション パッケージの構築に関する詳細については、次を参照してください。[する方法: SharePoint ソリューション パッケージ (wsp) を作成](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)です。|  
  
## <a name="creating-wizards-for-item-templates-and-project-templates"></a>項目テンプレートとプロジェクト テンプレートの作成ウィザード  
 SharePoint プロジェクト項目の種類を定義して、項目またはプロジェクト テンプレートに関連付ける後は、ウィザードを作成することもできます。 開発者では、項目テンプレートを使用して、プロジェクトに、SharePoint プロジェクト項目を追加するとき、または開発者では、プロジェクト テンプレートを使用して、SharePoint プロジェクト項目を含む新しいプロジェクトを作成するときに表示されます。 開発者からの情報を収集して、新しい SharePoint プロジェクト項目を初期化するために、このウィザードを使用できます。  
  
 項目テンプレートとプロジェクト テンプレートにウィザードを作成する方法を示すチュートリアルについては、次を参照してください[チュートリアル: 項目テンプレート、第 2 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)と[チュートリアル: サイトを作成します。プロジェクトのテンプレートでの列プロジェクト項目パート 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)です。  
  
## <a name="see-also"></a>参照  
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: 項目テンプレート、第 2 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [チュートリアル: プロジェクト テンプレート、第 1 部に基づくサイト列プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [チュートリアル: プロジェクト テンプレート、第 2 部に基づくサイト列プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [プロジェクトと項目テンプレートの作成](/visualstudio/ide/creating-project-and-item-templates)  
  
  