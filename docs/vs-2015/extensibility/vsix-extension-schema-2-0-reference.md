---
title: VSIX 拡張機能スキーマ 2.0 リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cacd0c1cd2a1e36e7c160902c93c6bcc6bfc0cdd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181208"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 拡張機能スキーマ 2.0 リファレンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX の配置マニフェスト ファイルでは、VSIX パッケージの内容について説明します。 ファイル形式は、スキーマによって管理されます。 このスキーマのバージョン 2.0 では、カスタムの型と属性の追加をサポートします。  マニフェストのスキーマは拡張可能です。 マニフェストのローダーでは、XML 要素とそれを認識しない属性は無視されます。  
  
> [!IMPORTANT]
>  Visual Studio 2015 では、Visual Studio 2010、Visual Studio 2012、または Visual Studio 2013 の形式で VSIX ファイルを読み込むことができます。  
  
## <a name="package-manifest-schema"></a>パッケージ マニフェスト スキーマ  
 マニフェストの XML ファイルのルート要素は`<PackageManifest>`、1 つの属性を持つ`Version`、マニフェストの形式のバージョンであります。 形式には、大きな変更が加えられて、バージョンの形式が変更されます。 このトピックで説明を設定して、マニフェストで指定されているマニフェスト形式バージョン 2.0、`Version`属性値のバージョンを「2.0」を = です。  
  
### <a name="packagemanifest-element"></a>PackageManifest Element  
 内で、`<PackageManifest>`ルート要素では、次の要素を使用することができます。  
  
-   `<Metadata>` メタデータと広告については、パッケージ自体。 1 つだけ`Metadata`要素は、マニフェストで使用します。  
  
-   `<Installation>` -このセクションをインストールするアプリケーションの Sku を含むこの拡張機能パッケージをインストールできる方法を定義します。 1 つだけ`Installation`要素は、マニフェストで使用します。 マニフェストが必要、`Installation`要素、またはこのパッケージは、任意の SKU にインストールされません。  
  
-   `<Dependencies>` -このパッケージの依存関係のオプションのリストは、ここで定義されます。  
  
-   `<Assets>` -このセクションには、このパッケージに含まれる資産のすべてが含まれます。 このセクションでは、なしこのパッケージは、任意のコンテンツを画面はありません。  
  
-   `<AnyElement>*` -マニフェスト スキーマは、柔軟なので、他の要素を許可します。 マニフェストのローダーによって認識されないすべての子要素は、余分な XmlElement オブジェクトとして、拡張機能マネージャー API で公開されます。 これらの子要素では、VSIX 拡張機能は、Visual Studio で実行されるコードが実行時にアクセスできるマニフェスト ファイルで追加のデータを定義できます。 「 <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> 」および「 <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>」を参照してください。  
  
### <a name="metadata-element"></a>メタデータ要素  
 このセクションでは、パッケージ、その id、および情報のアドバタイズに関するメタデータです。 `<Metadata>` 次の要素が含まれます。  
  
-   `<Identity>` -これは、このパッケージの id 情報を定義し、次の属性が含まれています。  
  
    -   `Id` – この属性は、その作成者によって選択されたパッケージの一意の ID である必要があります。 名前を修飾する必要がある同様の CLR 型は名前空間内: Company.Product.Feature.Name します。 `Id`属性は 100 文字に制限されます。  
  
    -   `Version` – これは、このパッケージとそのコンテンツのバージョンを定義します。 この属性が CLR アセンブリのバージョン管理の形式に従います: Major.Minor.Build.Revision (1.2.40308.00)。 高いバージョン番号を使用してパッケージを使用して、パッケージに更新プログラムを見なされ、既存のインストールされているバージョンをインストールできます。  
  
    -   `Language` – この属性は、パッケージの既定の言語であり、このマニフェスト内のテキスト形式のデータに対応しています。 この属性は規則に従って CLR ロケール コード、リソース アセンブリの例: en、米国、en、fr。 指定できます`neutral`はどのバージョンの Visual Studio で実行される言語に依存しない拡張機能を宣言します。 既定値は `neutral` です。  
  
    -   `Publisher` – この属性は、会社または個別の名前は、このパッケージの発行元を識別します。 `Publisher`属性は 100 文字に制限されます。  
  
-   `<DisplayName>` -この要素は、拡張機能マネージャーの UI に表示されるわかりやすいパッケージ名を指定します。 `DisplayName`コンテンツは 100 文字に制限されます。  
  
-   `<Description>` -この省略可能な要素は、拡張機能マネージャーの UI に表示されるパッケージとその内容の短い説明です。 `Description`コンテンツに制限はありませんが、これが任意のテキストを含めることができます 1000 文字に制限されます。  
  
-   `<MoreInfo>` -この省略可能な要素は、このパッケージの完全な説明を含むページをオンラインに URL です。 プロトコルは http として指定する必要があります。  
  
-   `<License>` -この省略可能な要素は、パッケージに含まれているライセンス ファイル (.txt、.rtf) への相対パスです。  
  
-   `<ReleaseNotes>` -この省略可能な要素とは、リリース ノートを表示する web サイトの URL か、または (.txt、.rtf) のパッケージに含まれるリリース ノート ファイルのいずれかを相対パスです。  
  
-   `<Icon>` -この省略可能な要素は、パッケージに含まれているイメージ ファイル (png、bmp、jpeg、ico) への相対パスです。 アイコン イメージは 32 x 32 ピクセル (またはそのサイズに圧縮されます)、listview の UI に表示されます。 ない場合は`Icon`要素を指定すると、UI は、既定値を使用します。  
  
-   `<PreviewImage>` -この省略可能な要素は、パッケージに含まれているイメージ ファイル (png、bmp、jpeg) への相対パスです。 プレビュー イメージは、200 x 200 (ピクセル単位) は、UI の詳細に表示されます。 ない場合は`PreviewImage`要素を指定すると、UI は、既定値を使用します。  
  
-   `<Tags>` -この省略可能な要素は、検索のヒントで使用されている追加のセミコロンで区切られたテキスト タグを一覧表示します。 `Tags`要素は 100 文字に制限されます。  
  
-   `<GettingStartedGuide>` -この省略可能な要素は、いずれかの HTML ファイルへの相対パスまたは拡張機能またはこのパッケージ内のコンテンツを使用する方法についての情報が含まれる web サイトの URL です。 このガイドは、インストールの一部として起動されます。  
  
-   `<AnyElement>*` -マニフェスト スキーマは、柔軟なので、他の要素を許可します。 マニフェストのローダーによって認識されないすべての子要素は、XmlElement オブジェクトの一覧として公開されます。 これらの子要素を使用して、VSIX 拡張機能は、マニフェスト ファイルで追加のデータを定義し、実行時にそれらを列挙します。  
  
### <a name="installation-element"></a>インストール要素  
 このセクションでは、このパッケージをインストールする方法、およびアプリケーションの Sku をインストールできることを定義します。 このセクションには、次の属性が含まれています。  
  
-   `Experimental` – この属性があるすべてのユーザーの現在インストールされている拡張機能が、同じコンピューターに更新されたバージョンを開発している場合は true に設定します。 たとえば、すべてのユーザー、MyExtension 1.0 をインストールしたが、MyExtension 2.0 を同じコンピューターでデバッグ、試験段階を設定する場合は、"true"=。 この属性は、Visual Studio 2015 Update 1 で使用できる以降です。  
  
-   `Scope` – この属性は、「グローバル」または"ProductExtension"の値を実行できます。  
  
    -   「グローバル」では、インストールは、特定の SKU にスコープでないことを指定します。 たとえば、この値は、拡張機能 SDK がインストールされている場合に使用されます。  
  
    -   "ProductExtension"では、従来 VSIX 拡張機能 (バージョン 1.0) を個別の Visual Studio Sku にスコープがインストールされていることを指定します。 これが既定値です。  
  
-   `AllUsers` – このオプションの属性は、このパッケージをすべてのユーザーに対してインストールするかどうかを指定します。 既定では、この属性が false の場合、ユーザーごと、パッケージは、これを指定します。 (この値を true に設定すると、インストールするユーザー必要がありますに昇格させる結果の VSIX をインストールする管理者の特権レベル。  
  
-   `InstalledByMsi` – このオプションの属性は、MSI でこのパッケージがインストールされているかどうかを指定します。 MSI でインストールされているパッケージがインストールされ、(プログラムと機能) の MSI によってとしない Visual Studio 拡張機能マネージャーによって管理されます。  既定では、この属性が false の場合、MSI では、パッケージがインストールされていないことを指定します。  
  
-   `SystemComponent` – このオプションの属性は、このパッケージに対して、システム コンポーネントを考慮するかどうかを指定します。 システム コンポーネントでは、拡張機能マネージャーの UI に表示しないし、更新することはできません。 既定では、この属性が false の場合、システム コンポーネントがパッケージではないことを指定します。  
  
-   `AnyAttribute*` –`Installation`要素は、制約のない一連の名前と値のペアのディクショナリとしての実行時に公開される属性を受け入れます。  
  
-   `<InstallationTarget>` この要素は、VSIX インストーラーが、パッケージをインストールする場所を制御します。 場合の値、`Scope`属性が"ProductExtension"パッケージの拡張機能の可用性を提供するには、その内容の一部としてマニフェスト ファイルがインストールされている SKU をターゲットする必要があります。 `<InstallationTarget>`要素には、次属性の場合に、`Scope`属性が、明示的な既定値"ProductExtension"。  
  
    -   `Id` – この属性は、パッケージを識別します。  属性が名前空間の規則に従います: Company.Product.Feature.Name します。 `Id`属性は、英数字のみを含めることができ、100 文字に制限されます。 予期される値:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   です  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` – この属性は、この SKU の最小値と最大のサポート対象バージョンのバージョンの範囲を指定します。 パッケージは、サポートされている Sku のバージョンについて詳しく説明ことができます。 バージョン範囲表記法が 10.0 – 11.0 が、  
  
        -   [– 包括的な最小バージョン。  
  
        -   – 包括最大バージョン。  
  
        -   (の排他的な最小バージョン。  
  
        -   ) – 排他最大バージョン。  
  
        -   1 つのバージョンと、指定されたバージョンのみ。  
  
        > [!IMPORTANT]
        >  VSIX スキーマのバージョン 2.0 は、Visual Studio 2012 で導入されました。 このスキーマを使用するには、Visual Studio 2012 が必要か、後でコンピューターにインストールされたを使用する VSIXInstaller.exe その製品の一部であります。 Visual Studio 2012 またはそれ以降の VSIXInstaller がインストーラーの以降のバージョンを使用してのみ、Visual Studio の以前のバージョンを対象にすることができます。  
  
    -   `AnyAttribute*` –`<InstallationTarget>`要素により、制約のない一連の属性の名前と値のペアのディクショナリとしての実行時に公開します。  
  
### <a name="dependencies-element"></a>依存関係要素  
 この要素には、このパッケージを宣言する依存関係の一覧が含まれています。 すべての依存関係を指定すると場合、それらのパッケージ (で識別される、 `Id`) する必要がある前にインストールされています。  
  
-   `<Dependency>` 要素 – この子要素では、次の属性があります。  
  
    -   `Id` – この属性は、依存パッケージの一意の ID を指定する必要があります。 この id 値に一致する必要があります、`<Metadata><Identity>Id`このパッケージが依存するパッケージの属性です。 `Id`属性が名前空間の規則に従います: Company.Product.Feature.Name します。 この属性は、英数字のみを含めることができ、100 文字に制限されています。  
  
    -   `Version` – この属性は、この SKU の最小値と最大のサポート対象バージョンのバージョンの範囲を指定します。 パッケージは、サポートされている Sku のバージョンについて詳しく説明ことができます。 バージョン範囲の表記は、[12.0, 13.0]、場所。  
  
        -   [– 包括的な最小バージョン。  
  
        -   – 包括最大バージョン。  
  
        -   (の排他的な最小バージョン。  
  
        -   ) – 排他最大バージョン。  
  
        -   1 つのバージョンと、指定されたバージョンのみ。  
  
    -   `DisplayName` -この属性は、ダイアログ ボックスとエラー メッセージなどの UI 要素で使用されている依存パッケージの表示名です。 MSI によって依存パッケージがインストールされていない場合、属性は省略可能です。  
  
    -   `Location` – このオプションの属性は、入れ子になった VSIX パッケージには、この VSIX 内の相対パスまたは依存関係をダウンロードする場所への URL のいずれかを指定します。 この属性は、ユーザーの前提条件となるパッケージを探しやすくために使用されます。  
  
    -   `AnyAttribute*` –`Dependency`要素は、制約のない一連の名前と値のペアのディクショナリとしての実行時に公開される属性を受け入れます。  
  
### <a name="assets-element"></a>資産要素  
 この要素の一覧を含む`<Asset>`このパッケージによって各拡張機能またはコンテンツの要素のタグが表示されます。  
  
-   `<Asset>` -この要素には、次の属性と要素が含まれています。  
  
    -   `Type` – これは、拡張機能またはこの要素によって表されるコンテンツの種類です。 各`<Asset>`要素が 1 つあります。 `Type`、が複数`<Asset>`要素は同じである可能性があります`Type`します。 この属性は、名前空間の規則に従って、完全修飾名として表す必要があります。 既知の型は次のとおりです。  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.visualstudio.projecttemplate  
  
        6.  [Microsoft.visualstudio.itemtemplate]  
  
        7.  [Microsoft.visualstudio.assembly]  
  
         独自の型を作成して一意の名前を付けます。 Visual Studio 内で実行時に、コードが列挙し、拡張機能マネージャー API を介してこれらのカスタム型にアクセスできます。  
  
    -   パス – ファイルまたは資産を含むパッケージ内のフォルダーへの相対パスです。  
  
    -   `AnyAttribute*` – 拡張可能な一連の属性名前と値のペアのディクショナリとしての実行時に公開します。  
  
         `<AnyElement>*` – 間構造化コンテンツは許可されて、`<Asset>`開始し、終了タグ。 すべての要素は、XmlElement オブジェクトの一覧として公開されます。 VSIX 拡張機能は、マニフェスト ファイルの構造化された型に固有のメタデータを定義し、実行時にそれらを列挙できます。  
  
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
 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)

