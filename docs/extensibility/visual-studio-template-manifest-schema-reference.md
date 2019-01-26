---
title: Visual Studio テンプレート マニフェスト スキーマ リファレンス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba9f4123b69a2decbcc46433e85082a4897b378d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999471"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio テンプレート マニフェスト スキーマ リファレンス
このスキーマは、Visual Studio テンプレート マニフェストの形式を示します (*.vstman*) Visual Studio プロジェクトや項目テンプレートに生成されるファイル。 スキーマには、場所と、テンプレートに関するその他の関連情報も説明します。  
  
 :個別の項目とプロジェクト テンプレートのディレクトリがあるため、マニフェストは項目とプロジェクト テンプレートが混在していることはありません。  
  
> [!IMPORTANT]
>  このマニフェストは、Visual Studio 2017 以降使用できます。  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 要素  
 マニフェストのルート要素。  
  
### <a name="attributes"></a>属性  
  
-   **バージョン**:テンプレート マニフェストのバージョンを表す文字列。 必須。  
  
-   **ロケール**:ロケールまたはテンプレート マニフェストのロケールを表す文字列。 ロケールの値は、すべてのテンプレートに適用されます。 ロケールごとに個別のマニフェストを使用する必要があります。 任意。  
  
### <a name="child-elements"></a>子要素  
  
-   **VSTemplateContainer**省略可能です。  
  
-   **VSTemplateDir**省略可能です。  
  
### <a name="parent-element"></a>親要素  
 なし。  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 テンプレートのコンテナーはマニフェストの要素です。 マニフェストが、定義テンプレートごとに 1 つのテンプレート コンテナー。  
  
### <a name="attributes"></a>属性  
 **VSTemplateType**:テンプレートの種類を指定する文字列値 (`"Project"`、 `"Item"`、または`"ProjectGroup"`)。 必須  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePathOnDisk**:ディスク上のテンプレート ファイルの相対パス。 この場所に示すようにテンプレートのツリーで、テンプレートの位置を定義することも、**新しいプロジェクト**または**新しい項目の**ダイアログ。 テンプレートのディレクトリと個々 のファイルとしてデプロイされている場合は、このパスは、テンプレート ファイルを含むディレクトリを参照します。 テンプレートのデプロイとしての *.zip*ファイルでは、このパスはパスを指定する必要があります、 *.zip*ファイル。  
  
-   * * VSTemplateHeader:A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)ヘッダーを説明する要素。  
  
### <a name="parent-element"></a>親要素  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 テンプレートがあるディレクトリをについて説明します。 マニフェストに複数含めることができます**VSTemplateDir**エントリはローカライズされた名前とディレクトリの順序を並べ替えると、テンプレート カテゴリのツリーで外観の制御を提供します。  
  
 自分の設計が**VSTemplateDir**エントリがロケールに指定したマニフェストでのみ表示されます。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePath**:テンプレートのパス。 すべてのマニフェストの 1 つ目が優先されますので、パスごとに 1 つだけのエントリがかかることがあります。  
  
-   **LocalizedName**:A **NameDescriptionIcon**ローカライズされた名前を指定する要素。 任意。  
  
-   **SortOrder**:並べ替え順序を指定する文字列。 任意。  
  
-   **ParentFolderOverrideName**:オーバーライドされた親フォルダーの名前。 任意。 この要素には、**名前**属性には、名前を指定する文字列値です。  
  
### <a name="parent-element"></a>親要素  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 ローカライズされたテンプレートの可能性がありますの説明と名前を指定します。 参照してください**LocalizedName**上。  
  
### <a name="attributes"></a>属性  
  
-   **パッケージ**:パッケージを指定する文字列値。 任意。  
  
-   **ID**:ID を指定する文字列値 任意。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-element"></a>親要素  
 **LocalizedName**  
  
## <a name="examples"></a>使用例  
 次のコードは、プロジェクト テンプレートの例 *.vstman*ファイル。  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 次のコードは、項目テンプレートの例 *.vstman*ファイル。  
  
```xml  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```