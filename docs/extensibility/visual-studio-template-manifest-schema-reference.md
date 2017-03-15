---
title: "Visual Studio テンプレート マニフェスト スキーマ リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 3
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 0f4abf286dc8b1cf00e47468ddaa4831747a059d
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio テンプレート マニフェスト スキーマ リファレンス
このスキーマでは、Visual Studio のプロジェクトまたは項目テンプレートに対して生成された Visual Studio のテンプレート (.vstman) をマニフェスト ファイルの形式、および場所と、テンプレートに関する関連情報を説明します。  
  
 個別のアイテムとプロジェクト テンプレートのディレクトリがある、ためマニフェストはさまざまな項目とプロジェクト テンプレートをことはありませんが必要です。  
  
> [!IMPORTANT]
>  このマニフェストは、Visual Studio 2017 以降使用できます。  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 要素  
 マニフェストのルート要素です。  
  
### <a name="attributes"></a>属性  
  
-   **バージョン**: テンプレート マニフェストのバージョンを表す文字列。 必須です。  
  
-   **ロケール**: ロケールまたはテンプレート マニフェストのロケールを表す文字列。 ロケール値は、ロケールごとに個別のマニフェストを使用する必要がありますので、すべてのテンプレートに適用されます。 省略可能です。  
  
### <a name="child-elements"></a>子要素  
  
-   **VSTemplateContainer**省略可能です。  
  
-   **VSTemplateDir**省略可能です。  
  
### <a name="parent-element"></a>Parent 要素  
 なし。  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 マニフェスト要素のテンプレートのコンテナー。 マニフェストを定義するテンプレートごとに&1; つのテンプレート コンテナーがあります。  
  
### <a name="attributes"></a>属性  
 **VSTemplateType** : テンプレートの種類を指定する文字列値 (`"Project"`、 `"Item"`、または`"ProjectGroup"`)。 必須  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePathOnDisk**: ディスク上のテンプレート ファイルの相対パスです。 この場所は、ツリーで、テンプレートに示すように、テンプレートの位置を定義するも、**新しいプロジェクト**または**新しい項目の**ダイアログ。 ディレクトリと個々 のファイルとして配置されているテンプレート では、このパスは、テンプレート ファイルを含むディレクトリを参照します。 テンプレートを .zip ファイルとして展開すると、このパスは .zip ファイルへのパスを指定します。  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)ヘッダーを記述する要素。  
  
### <a name="parent-element"></a>Parent 要素  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 テンプレートが配置されているディレクトリをについて説明します。 マニフェストは、複数を含めることができます**VSTemplateDir**エントリはローカライズされた名前とテンプレート カテゴリのツリーで、外観を制御するディレクトリの順序の並べ替えを指定します。  
  
 デザインにより**VSTemplateDir**エントリがロケールに指定したマニフェストにのみ表示されます。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
-   **RelativePath**: テンプレートのパス。 すべてのマニフェストの&1; つ目を差し上げますのでは、パスごとに&1; つだけのエントリが割り当てできます。  
  
-   **LocalizedName**: A **NameDescriptionIcon**ローカライズされた名前を指定する要素。 省略可能です。  
  
-   **SortOrder** : 並べ替え順序を指定する文字列。 省略可能です。  
  
-   **ParentFolderOverrideName**: オーバーライドされた親フォルダーの名前。 省略可能です。 この要素には、**名前**属性には、名前を指定する文字列値です。  
  
### <a name="parent-element"></a>Parent 要素  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 ローカライズされたテンプレートの可能性があるの説明と名前を指定します。 参照してください**LocalizedName**上です。  
  
### <a name="attributes"></a>属性  
  
-   **パッケージ**: パッケージを指定する文字列値。 省略可能です。  
  
-   **ID**: ID を指定する文字列値 省略可能です。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-element"></a>Parent 要素  
 **LocalizedName**  
  
## <a name="examples"></a>例  
 プロジェクト テンプレートの .vstman ファイルの例を次に示します。  
  
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
