---
title: テンプレートとプロジェクト テンプレートの SharePoint プロジェクト項目項目作成 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b5e66be099734008e09456cbd1e0f4fb4b0d5c9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854287"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成します。
  カスタム SharePoint プロジェクト項目の種類を定義するときに、項目テンプレートとプロジェクト テンプレートを関連付けることができます。 この関連付けにより、他の開発者が Visual Studio でプロジェクト項目を使用します。 テンプレートのウィザードを作成することもできます。

 たとえば、Visual Studio は、プロジェクト テンプレートや項目テンプレートのフィールドを SharePoint サイトに追加するには含まれません。 フィールドを表す SharePoint プロジェクト項目の種類を定義し、フィールドの項目を SharePoint プロジェクトに追加する他の開発者が使用できる項目テンプレートを作成できます。 または、プロジェクト テンプレートを作成するには、開発者は、フィールドの項目を持つ新しい SharePoint プロジェクトを作成できるようにします。 どちらの場合で、開発者は、テンプレートを使用すると表示されるウィザードを指定することもできます。 このウィザードでは、新しいアイテムやプロジェクトを構成する開発者からの情報を収集できます。

 項目テンプレートとプロジェクト テンプレートは *.zip*プロジェクトのアイテムやプロジェクトを作成する Visual Studio によって使用されるファイルを含むファイル。 項目テンプレートとプロジェクト テンプレートの基礎の詳細については、次を参照してください。[プロジェクトと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)します。

## <a name="create-item-templates"></a>項目テンプレートを作成する
 SharePoint プロジェクト項目の項目テンプレートを作成するときにいくつかの必要な場合は、常にファイルとプロジェクト項目の特定の型で使用される省略可能なファイル。 SharePoint プロジェクト項目の種類を定義し、その項目テンプレートを作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)です。

 次の表は、SharePoint プロジェクト項目の項目テンプレートの作成に必要なファイルを一覧表示します。

|必要なファイル|説明|
|-------------------|-----------------|
|*.Spdata*ファイル|この XML ファイルには、内容とプロジェクト項目の既定の動作を指定します。 このファイルは、項目テンプレートに含める必要があります。 内容の詳細については *.spdata*ファイルを参照してください[SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)します。|
|A *.vstemplate*ファイル。|このファイルにテンプレートを表示するために必要な情報を Visual Studio では、**新しい項目の追加** ダイアログ ボックスと、テンプレートからプロジェクト項目を作成します。 このファイルは、項目テンプレートに含める必要があります。 詳細については、次を参照してください。 [Visual Studio テンプレートのメタデータ ファイル](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)します。|
|実装する Visual Studio 拡張機能アセンブリ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>インターフェイス。|このアセンブリは、プロジェクト項目の実行時の動作を定義します。 このアセンブリは、項目テンプレートを使用して VSIX パッケージに含める必要があります。 詳細については、次を参照してください。[カスタム SharePoint プロジェクト項目の種類を定義する](../sharepoint/defining-custom-sharepoint-project-item-types.md)と[Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。|

 次の表には、いくつかの項目テンプレートに含めることができる最も一般的な省略可能なファイルが一覧表示します。 プロジェクト項目の種類によっては、この一覧にないその他のファイルを必要があります。


| 省略可能なファイル | 説明 |
|----------------------| - |
| *Elements.xml* | A *Feature 要素*ファイル。 このファイルは、プロジェクト アイテムによって作成されたカスタマイズの動作と UI を定義します。 それぞれのリスト インスタンス、コンテンツの種類、またはカスタムの動作などのカスタマイズの種類は、このファイルの内容を定義する別のスキーマを持ちます。 詳細については、次を参照してください。[ビルディング ブロック: 機能](http://go.microsoft.com/fwlink/?LinkId=169183)と[機能スキーマ](http://go.microsoft.com/fwlink/?LinkId=169192)します。 |
| *Schema.xml* | リスト定義のスキーマ ファイルです。 詳細については、次を参照してください。[ビルディング ブロック: リストとドキュメント ライブラリ](http://go.microsoft.com/fwlink/?LinkId=177792)と[Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)します。 |
| *.webpart* | A *Web パーツ定義*ファイル。 このファイルには、Web パーツのプロパティの設定が含まれています。 詳細については、次を参照してください。[構成要素: Web パーツ](http://go.microsoft.com/fwlink/?LinkId=177791)します。 |
| *.ascx* | ASP.NET ユーザー コントロール ファイルの場合。 このファイルは、視覚的 Web パーツの UI を定義します。 |
| *.aspx* | ASP.NET ページファイル このファイルには、アプリケーション ページを定義する XML マークアップが含まれています。 |
| *.cs*または *.vb*ファイル | これらのコード ファイルは、Visual c# または Visual Basic コード、アプリケーション ページ、Web パーツ、ワークフローなどからアクセスできるプログラミング モデルがある SharePoint のカスタマイズの動作を定義します。 |

## <a name="create-project-templates"></a>プロジェクト テンプレートを作成する
 SharePoint プロジェクト テンプレートを作成するときに特定の種類のプロジェクトで使用することが、必須およびオプションのファイルは、常にいくつかのファイルがあります。 通常、SharePoint プロジェクトには、少なくとも 1 つの SharePoint プロジェクト アイテムが含まれます。 ただし、これは必要ではありません。 たとえば、他のプロジェクトで作成した SharePoint ソリューションのデプロイにのみ使用するためのものでは、SharePoint プロジェクト テンプレートを定義できます。

 SharePoint プロジェクト項目の種類を定義し、そのプロジェクト テンプレートを作成する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)します。

 次の表では、SharePoint プロジェクトのテンプレートに含める必要があるファイルを示します。

|必要なファイル|説明|
|-------------------|-----------------|
|A *.vstemplate*ファイル|このファイルにテンプレートを表示するために必要な情報を Visual Studio では、**新しいプロジェクト** ダイアログ ボックスと、テンプレートからプロジェクトを作成します。 詳細については、次を参照してください。 [Visual Studio テンプレートのメタデータ ファイル](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)します。|
|A *.csproj*または *.vbproj*ファイル|これは、プロジェクト ファイルです。 内容と、プロジェクトの構成設定を定義します。|
|*Package.package*|このファイルは、プロジェクトの配置パッケージを定義します。 パッケージ デザイナーを使用して、プロジェクトのソリューション パッケージをカスタマイズするときに Visual Studio は、このファイルで、ソリューション パッケージのデータを格納します。<br /><br /> 最低限必要なコンテンツのみを含めることをお勧めカスタム SharePoint プロジェクト テンプレートを作成するときに、 *Package.package*ファイル、および Api を使用して、ソリューション パッケージを構成すること、 <xref:Microsoft.VisualStudio.SharePoint.Packages>プロジェクト テンプレートに関連付けられている拡張機能の名前空間。 構造に、プロジェクト テンプレートが将来の変更から保護されたこれを行う場合、 *Package.package*ファイル。 作成する方法を示す例については、 *Package.package*ファイルに必要な最低限の内容を参照してください[チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)します。<br /><br /> 変更する場合、 *Package.package*ファイルを直接には、スキーマを使用して内容を確認することができます *%program files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|このファイルは、ソリューションのマニフェスト ファイルの基礎を提供します (*manifest.xml*)、SharePoint ソリューション パッケージ (*.wsp*) プロジェクトから生成されます。 プロジェクトの種類のユーザーによって変更されるものではありませんが、いくつかの動作を指定する場合は、このファイルにコンテンツを追加できます。 詳細については、次を参照してください。[ビルディング ブロック: ソリューション](http://go.microsoft.com/fwlink/?LinkId=169186)と[ソリューション スキーマ](http://go.microsoft.com/fwlink/?LinkId=177794)します。<br /><br /> Visual Studio での内容をマージ、プロジェクトをソリューション パッケージをビルドするときに、 *Package.package*と*Package.Template.xml*ソリューションにファイルをマニフェスト ファイル。 ソリューション パッケージの作成の詳細については、次を参照してください。[方法: MSBuild タスクを使用した SharePoint ソリューション パッケージの作成](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)です。|

 次の表では、プロジェクトのテンプレートに含めることができる省略可能なファイルを示します。

|省略可能なファイル|説明|
|-------------------|-----------------|
|SharePoint プロジェクト項目|SharePoint プロジェクト項目の種類を定義する 1 つまたは複数の .spdata ファイルを含めることができます。 各 *.spdata*ファイルの対応する必要がありますが<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>プロジェクト テンプレートを使用して、VSIX パッケージに含まれている拡張機能アセンブリで実装します。 詳細については、次を参照してください。[項目テンプレートの作成](#creatingitemtemplates)です。<br /><br /> 通常、SharePoint プロジェクトには、少なくとも 1 つの SharePoint プロジェクト アイテムが含まれます。 ただし、これは必要ではありません。|
|*\<featureName > .feature*|このファイルは、展開の複数のプロジェクト項目をグループ化に使用される SharePoint 機能を定義します。 フィーチャー デザイナーを使用して、プロジェクトのフィーチャーをカスタマイズするときに、Visual Studio には、機能の詳細についてデータがこのファイルに格納します。 プロジェクト項目をさまざまな機能にグループ化する場合は、複数を含めることができます *.feature*ファイル。<br /><br /> カスタム SharePoint プロジェクト テンプレートを作成するときに、それぞれに必要な最小のコンテンツのみを含めることが勧め *.feature*ファイル、および Api を使用して機能を設定すること、<xref:Microsoft.VisualStudio.SharePoint.Features>名前空間で、プロジェクト テンプレートに関連付けられている拡張機能。 構造に、プロジェクト テンプレートが将来の変更から保護されたこれを行う場合、 *.feature*ファイル。 作成する方法を示す例については、 *.feature*ファイルに必要な最低限の内容を参照してください[チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)します。<br /><br /> 変更する場合、 *.feature*ファイルを直接には、スキーマを使用して内容を確認することができます *%program files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*します。|
|*\<featureName >。Template.xml*|このファイルはフィーチャー マニフェスト ファイルの基礎を提供します (*Feature.xml*)、プロジェクトから生成される各機能。 プロジェクトの種類のユーザーによって変更されるものではありませんが、いくつかの動作を指定する場合は、このファイルにコンテンツを追加できます。 詳細については、次を参照してください。[ビルディング ブロック: 機能](http://go.microsoft.com/fwlink/?LinkId=169183)と[Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795)ファイル。<br /><br /> Visual Studio プロジェクトからソリューション パッケージをビルドするときの各ペアの内容と結合 *\<featureName > .feature*ファイルと *\<featureName >。Template.xml*機能へのファイルにマニフェスト ファイル。 ソリューション パッケージの作成の詳細については、次を参照してください。[方法: MSBuild タスクを使用した SharePoint ソリューション パッケージの作成](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)です。|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>項目テンプレートとプロジェクト テンプレートのウィザードを作成します。
 SharePoint プロジェクト項目の種類を定義して、アイテムやプロジェクト テンプレートに関連付けることも、ウィザードを作成できます。 開発者は、SharePoint プロジェクト アイテムをプロジェクトに追加する項目テンプレートを使用する場合、または開発者は、SharePoint プロジェクト項目を含む新しいプロジェクトを作成するプロジェクト テンプレートを使用する場合、ウィザードを表示します。 開発者から情報を収集し、新しい SharePoint プロジェクト項目を初期化するために、ウィザードを使用できます。

 項目テンプレートとプロジェクト テンプレートにウィザードを作成する方法を説明するチュートリアルでは、次を参照してください[チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)と[チュートリアル: サイトを作成します。プロジェクト テンプレート、第 2 部での列プロジェクト項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)します。

## <a name="see-also"></a>関連項目

- [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [チュートリアル: プロジェクト テンプレート、第 1 部でのサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [チュートリアル: プロジェクト テンプレート、第 2 部でのサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
