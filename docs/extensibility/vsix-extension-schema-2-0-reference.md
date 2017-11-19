---
title: "VSIX 拡張機能スキーマ 2.0 リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1c81a34a290b34207f505d6b1ab46fa8b11cd8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 拡張機能スキーマ 2.0 リファレンス
VSIX の配置マニフェスト ファイルでは、VSIX パッケージの内容について説明します。 ファイルの形式は、スキーマによって制御されます。 このスキーマのバージョン 2.0 では、カスタムの型と属性の追加をサポートします。  マニフェストのスキーマは拡張できます。 マニフェストのローダーでは、XML 要素とそれに理解していない属性は無視されます。  
  
> [!IMPORTANT]
>  Visual Studio 2015 では、Visual Studio 2010、Visual Studio 2012、または Visual Studio 2013 の形式で VSIX ファイルを読み込むことができます。  
  
## <a name="package-manifest-schema"></a>パッケージ マニフェスト スキーマ  
 マニフェスト XML ファイルのルート要素が`<PackageManifest>`、1 つの属性を持つ`Version`、マニフェストの形式のバージョンであります。 形式に大幅な変更が行われた場合は、バージョンの形式が変更されます。 このトピックの説明を設定して、マニフェストで指定されているマニフェスト形式バージョン 2.0 では、`Version`属性値のバージョンを「2.0」を = です。  
  
### <a name="packagemanifest-element"></a>PackageManifest Element  
 内で、`<PackageManifest>`ルート要素は次の要素を使用することができます。  
  
-   `<Metadata>`メタデータ、および、パッケージ自体について提供情報。 1 つだけ`Metadata`要素は、マニフェストでは許可します。  
  
-   `<Installation>`-このセクションにインストールできるアプリケーションの Sku を含む、この拡張機能パッケージをインストールすることができますの方法を定義します。 1 つだけ`Installation`要素は、マニフェストでは許可します。 マニフェストが必要な`Installation`SKU に要素、またはこのパッケージはインストールされません。  
  
-   `<Dependencies>`-このパッケージの依存関係のオプション リストは、ここで定義されます。  
  
-   `<Assets>`-このセクションには、このパッケージ内に含まれる資産のすべてが含まれます。 このセクションでは、なしこのパッケージは、任意のコンテンツを画面はありません。  
  
-   `<AnyElement>*`-マニフェスト スキーマは、他の要素を許可するのに十分な柔軟性です。 マニフェストのローダーによって認識されないすべての子要素は、余分な XmlElement オブジェクトとして、拡張機能マネージャー API で公開されます。 これらの子要素では、VSIX 拡張機能は、Visual Studio で実行されているコードが実行時にアクセスできるマニフェスト ファイルで追加のデータを定義できます。 「<xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A>」および「<xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>」を参照してください。  
  
### <a name="metadata-element"></a>メタデータ要素  
 このセクションでは、パッケージ、その id、および情報のアドバタイズに関するメタデータです。 `<Metadata>`次の要素が含まれます。  
  
-   `<Identity>`-これは、このパッケージの id 情報を定義し、次の属性が含まれています。  
  
    -   `Id`-この属性は、作成者によって選択されたパッケージの一意の ID である必要があります。 CLR 型は名前空間内と同様、名前を修飾する必要があります: Company.Product.Feature.Name です。 `Id`属性は 100 文字に制限されます。  
  
    -   `Version`-これは、このパッケージとその内容のバージョンを定義します。 この属性に依存して、CLR アセンブリのバージョン管理の形式: Major.Minor.Build.Revision (1.2.40308.00)。 高いバージョン番号を使用してパッケージを使用して、パッケージに更新プログラムを見なされ、既存のインストールされているバージョンをインストールすることができます。  
  
    -   `Language`-この属性は、パッケージの既定の言語であり、このマニフェストのテキスト形式のデータに対応しています。 この属性に依存して、CLR ロケール コード規則リソース アセンブリは、たとえば: en-us、en、fr-fr がします。 指定できます`neutral`を任意のバージョンの Visual Studio で実行される言語に依存しない拡張機能を宣言します。 既定値は `neutral` です。  
  
    -   `Publisher`-この属性は、会社または個々 の名前は、このパッケージの発行元を識別します。 `Publisher`属性は 100 文字に制限されます。  
  
-   `<DisplayName>`-この要素は、拡張機能マネージャーの UI に表示される、使いやすいパッケージ名を指定します。 `DisplayName`コンテンツは 50 文字に制限されます。  
  
-   `<Description>`-この省略可能な要素は、拡張機能マネージャーの UI に表示されているパッケージとその内容の短い説明です。 `Description`コンテンツに制限はありませんが任意のテキストを含めることができますを 1000 文字に制限されます。  
  
-   `<MoreInfo>`-この省略可能な要素は、このパッケージの完全な説明を含むページをオンラインに URL です。 プロトコルは http として指定する必要があります。  
  
-   `<License>`-この省略可能な要素は、パッケージに含まれているライセンス ファイル (.txt、.rtf) への相対パスです。  
  
-   `<ReleaseNotes>`-この省略可能な要素は、いずれかへの相対パス (.txt、.rtf) パッケージそうしないと、リリース ノートを表示する web サイトへの URL に含まれるリリース ノート ファイルです。  
  
-   `<Icon>`-この省略可能な要素は、パッケージに含まれているイメージ ファイル (png、bmp、jpeg、ico) への相対パスです。 アイコン イメージ サイズは 32 x 32 ピクセルにする必要があります (またはそのサイズが圧縮されます)、listview UI に表示されます。 ない場合は`Icon`要素を指定すると、UI は、既定値を使用します。  
  
-   `<PreviewImage>`-この省略可能な要素は、パッケージに含まれているイメージ ファイル (png、bmp、jpeg) への相対パスです。 プレビュー イメージは、200 x 200 ピクセルにする必要があり、UI の詳細に表示されます。 ない場合は`PreviewImage`要素を指定すると、UI は、既定値を使用します。  
  
-   `<Tags>`-この省略可能な要素には、検索のヒントで使用されている追加のセミコロンで区切られたテキスト タグが一覧表示します。 `Tags`要素は 100 文字に制限されます。  
  
-   `<GettingStartedGuide>`-この省略可能な要素は、HTML ファイルへの相対パスまたは拡張機能またはこのパッケージ内のコンテンツを使用する方法に関する情報を含む web サイトへの URL。 このガイドは、インストールの一部として起動します。  
  
-   `<AnyElement>*`-マニフェスト スキーマは、他の要素を許可するのに十分な柔軟性です。 マニフェストのローダーによって認識されないすべての子要素は、XmlElement オブジェクトの一覧として公開されます。 これらの子要素を使用して、VSIX 拡張機能は、マニフェスト ファイルで追加のデータを定義して、実行時にそれらを列挙します。  
  
### <a name="installation-element"></a>インストール要素  
 このセクションでは、このパッケージをインストールする方法、およびにインストールできるアプリケーションの Sku を定義します。 このセクションには、次の属性が含まれています。  
  
-   `Experimental`-この属性は、すべてのユーザーの現在インストールされている拡張機能の大部分が同じコンピューターに更新されたバージョンを開発している場合は true に設定します。 たとえば、すべてのユーザー、MyExtension 1.0 をインストールしたが、同じコンピューター上で MyExtension 2.0 のデバッグ、試験段階を設定する場合は、"true"= です。 この属性は Visual Studio 2015 Update 1 以降使用します。  
  
-   `Scope`-この属性は、「グローバル」または"ProductExtension"の値を受け取ることができます。  
  
    -   「グローバル」は、インストールは、特定の SKU にスコープでないことを指定します。 たとえば、この値は、拡張 SDK がインストールされている場合に使用されます。  
  
    -   "ProductExtension"では、従来 VSIX 拡張機能 (version 1.0) 個々 の Visual Studio Sku にスコープがインストールされていることを指定します。 これが既定値です。  
  
-   `AllUsers`-この省略可能な属性では、このパッケージはすべてのユーザーに対してインストールするかどうかを指定します。 既定では、この属性が false の場合は、ユーザーごとのパッケージを指定します。 (この値を true に設定するときに、インストールするユーザー必要がありますに昇格させる、結果として得られる VSIX をインストールする管理者の特権レベル。  
  
-   `InstalledByMsi`-この省略可能な属性では、MSI でこのパッケージがインストールされているかどうかを指定します。 MSI でインストールされているパッケージがインストールされ、管理 MSI (プログラムと機能) されないによって、Visual Studio 拡張機能マネージャー。  既定では、この属性が false の場合、MSI によってパッケージがインストールされていないことを指定します。  
  
-   `SystemComponent`-この省略可能な属性では、このパッケージに対して、システム コンポーネントを考慮するかどうかを指定します。 システム コンポーネントは、拡張機能マネージャーの UI に表示しないし、更新できません。 既定では、この属性が false の場合、パッケージ、システムのコンポーネントではないことを指定します。  
  
-   `AnyAttribute*`-`Installation`要素は、名前と値のペアのディクショナリとしての実行時に公開される属性の制約のない一連を受け入れます。  
  
-   `<InstallationTarget>`-この要素は、VSIX インストーラーが、パッケージをインストール場所を制御します。 場合の値、`Scope`属性が"ProductExtension"パッケージが拡張機能には、その可用性を提供するには、その内容の一部としてマニフェスト ファイルがインストールされて SKU をターゲットする必要があります。 `<InstallationTarget>`要素には、次属性の場合、`Scope`属性が明示的か既定値"ProductExtension"。  
  
    -   `Id`-この属性は、パッケージを識別します。  属性に依存して、名前空間規則: Company.Product.Feature.Name です。 `Id`属性は、英数字のみを含めることができ、100 文字に制限されます。 予期される値:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version`-この属性は、この SKU の最小値と最大のサポート対象バージョンのバージョンの範囲を指定します。 パッケージには、sku でサポートされるバージョンを詳しく説明します。 バージョン範囲は、表記は 10.0-11.0 と場所  
  
        -   [の包括的な最小バージョン。  
  
        -   の最大バージョンの包括的です。  
  
        -   (-排他の最小バージョン。  
  
        -   )-排他の最大バージョン。  
  
        -   1 つのバージョン番号の指定バージョンのみ。  
  
        > [!IMPORTANT]
        >  VSIX スキーマのバージョン 2.0 は、Visual Studio 2012 で導入されました。 このスキーマを使用するには、Visual Studio 2012 をいる必要がありますまたは後でコンピューターにインストールして使用するはその製品の一部である VSIXInstaller.exe です。 以降のバージョンのインストーラーを使用してのみが、Visual Studio 2012 またはそれ以降の VSIXInstaller で Visual Studio の以前のバージョンを対象にすることができます。  
  
    -   `AnyAttribute*`-`<InstallationTarget>`要素により、名前と値のペアのディクショナリとしての実行時に公開されます属性を一連の制限はありません。  
  
### <a name="dependencies-element"></a>Dependencies 要素  
 この要素には、このパッケージを宣言する依存関係の一覧が含まれています。 すべての依存関係も指定しない場合、それらのパッケージ (で識別される、 `Id`) する必要がある前にインストールされています。  
  
-   `<Dependency>`要素のこの子要素では、次の属性があります。  
  
    -   `Id`-この属性は、その依存パッケージの一意の ID である必要があります。 この id 値に一致する必要があります、`<Metadata><Identity>Id`このパッケージが依存するパッケージの属性です。 `Id`属性に依存して、名前空間規則: Company.Product.Feature.Name です。 属性は、英数字のみを含めることができ、100 文字に制限されます。  
  
    -   `Version`-この属性は、この SKU の最小値と最大のサポート対象バージョンのバージョンの範囲を指定します。 パッケージには、sku でサポートされるバージョンを詳しく説明します。 バージョン範囲の表記は、[12.0, 13.0]、場所。  
  
        -   [の包括的な最小バージョン。  
  
        -   の最大バージョンの包括的です。  
  
        -   (-排他の最小バージョン。  
  
        -   )-排他の最大バージョン。  
  
        -   1 つのバージョン番号の指定バージョンのみ。  
  
    -   `DisplayName`-この属性は、ダイアログ ボックスとエラー メッセージなどの UI 要素で使用されている依存パッケージの表示名です。 MSI によって依存パッケージがインストールされていない場合、属性は省略できます。  
  
    -   `Location`-この省略可能な属性は、入れ子になった VSIX パッケージにこの VSIX 内の相対パスまたは依存関係をダウンロードする場所への URL のいずれかを指定します。 この属性はパッケージを探し、前提条件となるユーザーを支援するために使用します。  
  
    -   `AnyAttribute*`-`Dependency`要素は、名前と値のペアのディクショナリとしての実行時に公開される属性の制約のない一連を受け入れます。  
  
### <a name="assets-element"></a>資産要素  
 この要素の一覧を含む`<Asset>`拡張機能またはコンテンツの各要素のタグがこのパッケージによって示されます。  
  
-   `<Asset>`-この要素には、次の属性と要素が含まれています。  
  
    -   `Type`-これは、拡張機能またはこの要素によって表されるコンテンツの種類です。 各`<Asset>`要素が 1 つの必要`Type`が、複数`<Asset>`要素と同じである可能性があります`Type`です。 この属性は、名前空間規則に従って、完全修飾名として表現する必要があります。 既知の型は次のとおりです。  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  [Microsoft.visualstudio.projecttemplate]  
  
        6.  [Microsoft.visualstudio.itemtemplate]  
  
        7.  [Microsoft.visualstudio.assembly]  
  
         独自の型を作成し、一意の名前を付与できます。 、Visual Studio 内の実行時に、コードが列挙し、拡張機能マネージャー API を介してこれらのカスタム型にアクセスできます。  
  
    -   パス - ファイルまたは資産を含むパッケージ内のフォルダーへの相対パスです。  
  
    -   `AnyAttribute*`-制約のない一連の属性、名前と値のペアのディクショナリとしての実行時に公開されます。  
  
         `<AnyElement>*`で間構造化されたコンテンツは許可されて、`<Asset>`開始し、終了タグ。 すべての要素は、XmlElement オブジェクトの一覧として公開されます。 VSIX 拡張機能では、マニフェスト ファイルの構造化された型に固有のメタデータを定義でき、実行時にそれらを列挙することができます。  
  
### <a name="sample-manifest"></a>サンプルのマニフェスト  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)