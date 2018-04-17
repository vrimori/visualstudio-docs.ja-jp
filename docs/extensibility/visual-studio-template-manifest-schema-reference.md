---
title: Visual Studio テンプレート マニフェスト スキーマ リファレンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26f346329e4c0fa2defe6bc4ff6373226be72beb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio テンプレート マニフェスト スキーマ リファレンス
このスキーマは、Visual Studio のプロジェクトまたは項目テンプレートに対して生成された Visual Studio テンプレート マニフェスト (.vstman) ファイルの形式をについて説明し、場所と、テンプレートに関するその他の関連情報について説明します。  
  
 : ため、個別のアイテムとプロジェクト テンプレートのディレクトリがある、マニフェストをする必要があります項目とプロジェクト テンプレートが混在していることはありません。  
  
> [!IMPORTANT]
>  このマニフェストは、Visual Studio 2017 ので利用可能です。  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 要素  
 マニフェストのルート要素です。  
  
### <a name="attributes"></a>属性  
  
-   **バージョン**: テンプレート マニフェストのバージョンを表す文字列。 必須。  
  
-   **ロケール**: ロケールまたはテンプレート マニフェストのロケールを表す文字列。 ロケール値は、ロケールごとに個別のマニフェストを使用する必要がありますので、すべてのテンプレートに適用されます。 任意。  
  
### <a name="child-elements"></a>子要素  
  
-   **VSTemplateContainer**省略可能です。  
  
-   **VSTemplateDir**省略可能です。  
  
### <a name="parent-element"></a>Parent 要素  
 なし。  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 テンプレートのコンテナーはマニフェストの要素です。 マニフェストを定義するテンプレートごとに 1 つのテンプレート コンテナーを持ちます。  
  
### <a name="attributes"></a>属性  
 **VSTemplateType** : テンプレートの種類を指定する文字列値 (`"Project"`、 `"Item"`、または`"ProjectGroup"`)。 必須  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePathOnDisk**: ディスク上のテンプレート ファイルの相対パスです。 この場所は、ツリーで、テンプレートに示すように、テンプレートの位置を定義するも、**新しいプロジェクト**または**新しい項目の**ダイアログ。 テンプレートのディレクトリと個々 のファイルとして展開されている場合は、このパスは、テンプレート ファイルを含むディレクトリを参照します。 テンプレートの .zip ファイルとして展開されている場合、このパスは、.zip ファイルへのパスを指定します。  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)ヘッダーを説明する要素。  
  
### <a name="parent-element"></a>Parent 要素  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 テンプレートが配置されているディレクトリをについて説明します。 マニフェストは、複数を含めることができます**VSTemplateDir**エントリはローカライズされた名前とテンプレート カテゴリのツリーでその外観を制御するディレクトリの順序の並べ替えを提供します。  
  
 そのデザインにより**VSTemplateDir**エントリがロケールに指定したマニフェストにのみ表示されます。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePath**: テンプレートのパス。 すべてのマニフェストの最初の 1 つが優先されますのでは、パスごとに 1 つだけのエントリが割り当てできます。  
  
-   **LocalizedName**: A **NameDescriptionIcon**ローカライズされた名前を指定する要素。 任意。  
  
-   **SortOrder** : 並べ替え順序を指定する文字列。 任意。  
  
-   **ParentFolderOverrideName**: オーバーライドされた親フォルダーの名前。 任意。 この要素には、**名前**属性には、名前を指定する文字列値です。  
  
### <a name="parent-element"></a>Parent 要素  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 ローカライズされたテンプレートの可能性がありますの説明と名前を指定します。 参照してください**LocalizedName**上。  
  
### <a name="attributes"></a>属性  
  
-   **パッケージ**: パッケージを指定する文字列値です。 任意。  
  
-   **ID**: ID を指定する文字列値 任意。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-element"></a>Parent 要素  
 **LocalizedName**  
  
## <a name="examples"></a>使用例  
 プロジェクト テンプレート .vstman ファイルの例を次に示します。  
  
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
  
 項目テンプレート .vstman ファイルの例を次に示します。  
  
```  
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