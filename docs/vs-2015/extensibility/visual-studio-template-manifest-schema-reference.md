---
title: Visual Studio テンプレート マニフェスト スキーマ リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b079e6b7356cdd84a98314beef95f4b1a8fbc5ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535942"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio テンプレート マニフェスト スキーマ参照
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio テンプレート マニフェスト スキーマ参照](https://docs.microsoft.com/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)します。  
  
このスキーマは、Visual Studio のプロジェクトや項目テンプレートに対して生成された Visual Studio テンプレート マニフェスト (.vstman) ファイルの形式について説明し、場所と、テンプレートに関するその他の関連情報について説明します。  
  
 : ため、個別の項目とプロジェクト テンプレートのディレクトリがある、マニフェストが項目とプロジェクト テンプレートが混在していることはありません。  
  
> [!IMPORTANT]
>  このマニフェストでは、Visual Studio「15」Preview 2 以降で使用できます。  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 要素  
 マニフェストのルート要素。  
  
### <a name="attributes"></a>属性  
  
-   **バージョン**: テンプレート マニフェストのバージョンを表す文字列。 必須。  
  
-   **ロケール**: ロケールまたはテンプレート マニフェストのロケールを表す文字列。 ロケール値は、ロケールごとに個別のマニフェストを使用する必要がありますので、すべてのテンプレートに適用されます。 任意。  
  
### <a name="child-elements"></a>子要素  
  
-   **VSTemplateContainer**省略可能です。  
  
-   **VSTemplateDir**省略可能です。  
  
### <a name="parent-element"></a>Parent 要素  
 なし。  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 テンプレートのコンテナーはマニフェストの要素です。 マニフェストが、定義テンプレートごとに 1 つのテンプレート コンテナー。  
  
### <a name="attributes"></a>属性  
 **VSTemplateType** : テンプレートの種類を指定する文字列値 (`"Project"`、 `"Item"`、または`"ProjectGroup"`)。 必須  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePathOnDisk**: ディスク上のテンプレート ファイルの相対パス。 この場所に示すようにテンプレートのツリーで、テンプレートの位置を定義することも、**新しいプロジェクト**または**新しい項目の**ダイアログ。 テンプレートのディレクトリと個々 のファイルとしてデプロイされている場合は、このパスは、テンプレート ファイルを含むディレクトリを参照します。 テンプレートの .zip ファイルとしてデプロイされている場合、このパスは、.zip ファイルへのパスを指定します。  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)ヘッダーを説明する要素。  
  
### <a name="parent-element"></a>Parent 要素  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 テンプレートがあるディレクトリをについて説明します。 マニフェストに複数含めることができます**VSTemplateDir**エントリはローカライズされた名前とディレクトリの順序を並べ替えると、テンプレート カテゴリのツリーで外観の制御を提供します。  
  
 自分の設計が**VSTemplateDir**エントリがロケールに指定したマニフェストでのみ表示されます。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePath**: テンプレートのパス。 すべてのマニフェストの 1 つ目が優先されますので、パスごとに 1 つだけのエントリがかかることがあります。  
  
-   **LocalizedName**: A **NameDescriptionIcon**ローカライズされた名前を指定する要素。 任意。  
  
-   **SortOrder** : 並べ替え順序を指定する文字列。 任意。  
  
-   **ParentFolderOverrideName**: オーバーライドされた親フォルダーの名前。 任意。 この要素には、**名前**属性には、名前を指定する文字列値です。  
  
### <a name="parent-element"></a>Parent 要素  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 ローカライズされたテンプレートの可能性がありますの説明と名前を指定します。 参照してください**LocalizedName**上。  
  
### <a name="attributes"></a>属性  
  
-   **パッケージ**: パッケージを指定する文字列値。 任意。  
  
-   **ID**: ID を指定する文字列値 任意。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-element"></a>Parent 要素  
 **LocalizedName**  
  
## <a name="examples"></a>使用例  
 次にプロジェクト テンプレートの .vstman ファイルの例を示します。  
  
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
  
 次は、項目テンプレート .vstman ファイルの例です。  
  
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

