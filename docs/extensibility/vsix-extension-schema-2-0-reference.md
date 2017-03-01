---
title: "VSIX 拡張機能スキーマ 2.0 リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3e6aa4a23c5146eacaac90b02c2c742c28a105d1
ms.lasthandoff: 02/22/2017

---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 拡張機能スキーマ 2.0 リファレンス
VSIX の配置マニフェスト ファイルでは、VSIX パッケージの内容について説明します。 ファイル形式は、スキーマによって制御されます。 このスキーマのバージョン 2.0 では、カスタム型と属性の追加をサポートします。  マニフェストのスキーマは拡張できます。 マニフェストのローダーは、XML 要素とそれが認識されない属性を無視します。  
  
> [!IMPORTANT]
>  Visual Studio 2015 では、Visual Studio 2010、Visual Studio 2012 または Visual Studio 2013 の形式で VSIX ファイルを読み込むことができます。  
  
## <a name="package-manifest-schema"></a>パッケージ マニフェスト スキーマ  
 マニフェストの XML ファイルのルート要素が`<PackageManifest>`、単一の属性を持つ`Version`、マニフェストのファイル形式のバージョンであります。 大幅な変更は、形式に加え、バージョンの形式が変更されます。 設定して、マニフェストで指定されているマニフェスト ファイル形式バージョン 2.0 では、説明、`Version`属性値のバージョンを =「2.0」です。  
  
### <a name="packagemanifest-element"></a>PackageManifest 要素  
 内で、`<PackageManifest>`ルート要素は次の要素を使用することができます。  
  
-   `<Metadata>`メタデータ、およびパッケージ自体は提供情報。 1 つだけ`Metadata`要素は、マニフェストで使用します。  
  
-   `<Installation>`-このセクションにインストールできるアプリケーションの Sku を含むこの拡張機能パッケージをインストールする方法を定義します。 1 つだけ`Installation`要素は、マニフェストで使用します。 マニフェストが必要な`Installation`要素、またはこのパッケージは、任意の SKU にインストールされません。  
  
-   `<Dependencies>`-このパッケージの依存関係のオプション リストは、ここで定義されます。  
  
-   `<Assets>`-このセクションには、このパッケージに含まれるアセットはすべてが含まれます。 ここでは、なしこのパッケージは、任意のコンテンツを画面はありません。  
  
-   `<AnyElement>*`-マニフェストのスキーマは、他の要素を許可するように十分な柔軟性です。 マニフェストのローダーによって認識されないすべての子要素は、余分な XmlElement オブジェクトとして、拡張機能マネージャー API で公開されます。 これらの子要素では、VSIX 拡張機能は、Visual Studio で実行されているコードは、実行時にアクセスできるマニフェスト ファイルで追加のデータを定義できます。 <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.</xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A></xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A>を参照してください。  
  
### <a name="metadata-element"></a>メタデータ要素  
 このセクションでは、パッケージ、その id、および情報のアドバタイズに関するメタデータです。 `<Metadata>`次の要素があります。  
  
-   `<Identity>`-これは、このパッケージの識別情報を定義し、次の属性が含まれています。  
  
    -   `Id`この属性は、その著者によって選択されたパッケージの一意の ID である必要があります。 CLR 型は名前空間内のと同様、名前を修飾する必要があります: Company.Product.Feature.Name です。 `Id`属性は 100 文字に制限します。  
  
    -   `Version`-これは、このパッケージとそのコンテンツのバージョンを定義します。 この属性に依存して、CLR アセンブリのバージョン管理の形式: Major.Minor.Build.Revision (1.2.40308.00)。 高いバージョン番号を含むパッケージは、パッケージの更新プログラムと既存のインストールされているバージョンをインストールすることができます。  
  
    -   `Language`この属性は、パッケージの既定の言語であり、このマニフェストでテキスト データに対応しています。 この属性に依存して CLR ロケール コード規則リソース アセンブリでは、たとえば: en-私たち, en, fr-fr にします。 指定できます`neutral`を任意のバージョンの Visual Studio で実行される言語に依存しない拡張機能を宣言します。 既定値は `neutral` です。  
  
    -   `Publisher`この属性は、会社または個別の名前は、このパッケージの発行元を識別します。 `Publisher`属性は 100 文字に制限します。  
  
-   `<DisplayName>`-この要素は、拡張機能マネージャーの UI に表示されるパッケージのわかりやすい名前を指定します。 `DisplayName`コンテンツは 100 文字に限定されます。  
  
-   `<Description>`-この省略可能な要素は、拡張機能マネージャーの UI に表示されるパッケージとその内容の短い説明です。 `Description`コンテンツに制限はありませんが、ある任意のテキストを含めることができます 1000 文字に制限されます。  
  
-   `<MoreInfo>`-この省略可能な要素は、このパッケージの詳しい説明を含むページをオンラインに URL です。 プロトコルは http として指定する必要があります。  
  
-   `<License>`-この省略可能な要素は、パッケージに含まれているライセンス ファイル (.txt、.rtf) への相対パスです。  
  
-   `<ReleaseNotes>`-この省略可能な要素は、リリース ノートを表示する web サイトへの URL か、または (.txt、.rtf) のパッケージに含まれるリリース ノート ファイルへの相対パスです。  
  
-   `<Icon>`-この省略可能な要素は、パッケージに含まれているイメージ ファイル (png、bmp、jpeg、ico) への相対パスです。 アイコンのイメージ サイズが 32 × 32 ピクセルにする必要があります (またはそのサイズが圧縮されます)、listview の UI に表示されます。 ない場合`Icon`要素を指定すると、UI が、既定値を使用します。  
  
-   `<PreviewImage>`-この省略可能な要素は、パッケージに含まれているイメージ ファイル (png、bmp、jpeg) への相対パスです。 プレビュー イメージは、200 x 200 ピクセルにする必要があり、UI の詳細に表示します。 ない場合`PreviewImage`要素を指定すると、UI が、既定値を使用します。  
  
-   `<Tags>`-この省略可能な要素には、検索のヒントに使用されている追加のセミコロンで区切られたテキスト タグが一覧表示します。 `Tags`要素は 100 文字に制限します。  
  
-   `<GettingStartedGuide>`-この省略可能な要素は、いずれかの HTML ファイルへの相対パスまたは拡張機能またはこのパッケージ内のコンテンツを使用する方法に関する情報を含む web サイトの URL です。 このガイドは、インストールの一部として起動します。  
  
-   `<AnyElement>*`-マニフェストのスキーマは、他の要素を許可するように十分な柔軟性です。 マニフェストのローダーによって認識されないすべての子要素は、XmlElement オブジェクトの一覧として公開されます。 これらの子要素を使用して、VSIX 拡張機能は、マニフェスト ファイルの追加データを定義して、実行時にそれらを列挙します。  
  
### <a name="installation-element"></a>インストール要素  
 このセクションでは、このパッケージをインストールする方法、およびにインストールできるアプリケーションの Sku を定義します。 このセクションには、次の属性が含まれています。  
  
-   `Experimental`– すべてのユーザーの現在インストールされている拡張機能が同じコンピューターに更新されたバージョンを開発している場合は true には、この属性を設定します。 たとえば、すべてのユーザーに対して、MyExtension 1.0 をインストールした場合は、同じコンピューターに MyExtension 2.0 をデバッグするには、開発中の設定 ="true"とします。 この属性は、Visual Studio 2015 の Update 1 で使用できる以降です。  
  
-   `Scope`– この属性は、「グローバル」または"ProductExtension"の値を受け取ることができます。  
  
    -   「グローバル」は、インストールのスコープはない特定の SKU にことを指定します。 たとえば、拡張 SDK がインストールされている場合、この値が使用されます。  
  
    -   "ProductExtension"は従来 VSIX 拡張機能 (バージョン 1.0) 個別の Visual Studio Sku にスコープがインストールされていることを指定します。 これが既定値です。  
  
-   `AllUsers`– このオプションの属性は、すべてのユーザーに対してこのパッケージがインストールされるかどうかを指定します。 既定では、この属性は false の場合、パッケージは、各ユーザーを指定します。 (この値を true に設定すると、インストールするユーザー必要がありますに昇格させる結果の VSIX をインストールする管理者の特権レベル。  
  
-   `InstalledByMsi`– このオプションの属性は、MSI でこのパッケージがインストールされているかどうかを指定します。 MSI がインストールされているパッケージでは、インストールされているされ、MSI (プログラムと機能) していませんが、Visual Studio Extension Manager を管理することができます。  既定では、この属性が false の場合、MSI によってパッケージがインストールされていないことを指定します。  
  
-   `SystemComponent`– このオプションの属性は、このパッケージに対して、システム コンポーネントを考慮するかどうかを指定します。 システム コンポーネントでは、拡張機能マネージャーの UI に表示しないし、更新することはできません。 既定では、この属性が false の場合、システム コンポーネントがパッケージではないことを指定します。  
  
-   `AnyAttribute*`–`Installation`要素は、制約のない一連の名前と値のペアのディクショナリとしての実行時に公開される属性を受け入れます。  
  
-   `<InstallationTarget>`この要素は、VSIX インストーラーが、パッケージをインストールする場所を制御します。 場合の値、`Scope`属性は、"ProductExtension"パッケージを拡張するには、その可用性を提供するには、その内容の一部としてマニフェスト ファイルがインストールされて SKU を対象にします。 `<InstallationTarget>`要素には、次属性の場合、`Scope`属性は、明示的にまたは既定値"ProductExtension"。  
  
    -   `Id`この属性は、パッケージを識別します。  属性に依存して、名前空間規則: Company.Product.Feature.Name です。 `Id`属性英数字のみを含めることができ、100 文字に制限されます。 必要な値:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version`この属性は、この SKU の最小値と最大のサポート対象バージョンのバージョンの範囲を指定します。 パッケージ バージョンがサポートする Sku の詳細に説明できます。 バージョン範囲表記は 10.0 – 11.0、です。  
  
        -   [– 包括的な最低限のバージョン。  
  
        -   – 包括的なバージョンの最大値。  
  
        -   (の排他的な最小バージョンです。  
  
        -   ) – 排他最大バージョン。  
  
        -   1 つのバージョン番号で指定されたバージョンのみ。  
  
        > [!IMPORTANT]
        >  VSIX のスキーマのバージョン 2.0 は、Visual Studio 2012 で導入されました。 このスキーマを使用するには、Visual Studio 2012 が必要または後で、コンピューターにインストールを使用する製品の一部である VSIXInstaller.exe。 以降のバージョンのインストーラーを使用してのみが、Visual Studio 2012 またはそれ以降の VSIXInstaller で Visual Studio の以前のバージョンを対象にすることができます。  
  
    -   `AnyAttribute*`–`<InstallationTarget>`要素により、制約のない一連の属性の名前と値のペアのディクショナリとしての実行時に公開します。  
  
### <a name="dependencies-element"></a>Dependencies 要素  
 この要素には、このパッケージを宣言する依存関係の一覧が含まれています。 すべての依存関係を指定する場合これらのパッケージ (で識別される、 `Id`) する必要がある前にインストールされています。  
  
-   `<Dependency>`要素: この子要素では、次の属性があります。  
  
    -   `Id`– この属性は、依存パッケージの一意の ID を指定する必要があります。 この id の値に一致する必要があります、`<Metadata><Identity>Id`このパッケージが依存するパッケージの属性です。 `Id`属性に依存して、名前空間規則: Company.Product.Feature.Name です。 属性は、英数字のみを含めることができは 100 文字に制限されます。  
  
    -   `Version`この属性は、この SKU の最小値と最大のサポート対象バージョンのバージョンの範囲を指定します。 パッケージ バージョンがサポートする Sku の詳細に説明できます。 バージョン範囲表記は、[12.0, 13.0]、場所。  
  
        -   [– 包括的な最低限のバージョン。  
  
        -   – 包括的なバージョンの最大値。  
  
        -   (の排他的な最小バージョンです。  
  
        -   ) – 排他最大バージョン。  
  
        -   1 つのバージョン番号で指定されたバージョンのみ。  
  
    -   `DisplayName`-この属性は、ダイアログ ボックスとエラー メッセージなどの UI 要素で使用されている依存パッケージの表示名です。 属性は、MSI によって依存パッケージがインストールされていないオプションです。  
  
    -   `Location`– このオプションの属性は、この VSIX を入れ子になった VSIX パッケージ内の相対パスか、依存関係をダウンロードする場所への URL を指定します。 この属性は、パッケージを探し、前提条件となるユーザーのために使用されます。  
  
    -   `AnyAttribute*`–`Dependency`要素は、制約のない一連の名前と値のペアのディクショナリとしての実行時に公開される属性を受け入れます。  
  
### <a name="assets-element"></a>資産要素  
 この要素の一覧を含む`<Asset>`このパッケージによって各拡張機能またはコンテンツの要素のタグが表示されます。  
  
-   `<Asset>`-この要素には、次の属性と要素が含まれています。  
  
    -   `Type`– これは、拡張機能またはこの要素によって表されるコンテンツの種類です。 各`<Asset>`要素が&1; つの必要`Type`、複数が、`<Asset>`要素と同じである可能性があります`Type`します。 この属性は、名前空間規則に従って、完全修飾名として表す必要があります。 既知の型は次のとおりです。  
  
        1.  として Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  [Microsoft.visualstudio.projecttemplate]  
  
        6.  [Microsoft.visualstudio.itemtemplate]  
  
        7.  [Microsoft.visualstudio.assembly]  
  
         ユーザー独自の型を作成して、一意の名前を付けます。 Visual Studio で実行時に、コードは列挙し、カスタム拡張機能マネージャーの API を介してアクセスします。  
  
    -   パス – ファイルまたは資産を含むパッケージ内のフォルダーへの相対パスです。  
  
    -   `AnyAttribute*`–、変更可能な一連の属性名前と値のペアのディクショナリとしての実行時に公開します。  
  
         `<AnyElement>*`– 間で、構造化コンテンツを許可、`<Asset>`開始し、終了タグ。 すべての要素は、XmlElement オブジェクトの一覧として公開されます。 VSIX 拡張機能では、マニフェスト ファイルの種類に固有の構造化されたメタデータを定義して、実行時にそれらを列挙することができます。  
  
### <a name="sample-manifest"></a>サンプル マニフェスト  
  
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
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)
