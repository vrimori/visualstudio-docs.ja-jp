---
title: RequiredFrameworkVersion 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23538e8e00553322f4f04e50414a8b3ddbd73b91
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39635921"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion 要素 (Visual Studio テンプレート)

テンプレートで必要とされる .NET Framework の最小バージョンを指定します。 **ターゲット フレームワークのバージョン**に表示するドロップダウン、**新しいプロジェクト**ダイアログ。 `RequiredFrameworkVersion`要素では、ドロップダウン リストで使用できる最小値も決定します。

> [!IMPORTANT]
> Visual Studio 2017 バージョン 15.6 では、以降、**ターゲット フレームワーク バージョン**ドロップダウンが表示されているテンプレートのフィルターでは不要になった、**テンプレート**のセクション、 **の新しいプロジェクト**ダイアログ。 代わりに、ドロップダウン リストでは、選択したテンプレートの framework ピッカーとして機能します。

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>構文

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
```

## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性
 なし。

### <a name="child-elements"></a>子要素
 なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートを分類し、いずれかでの表示方法を定義、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|

## <a name="text-value"></a>テキスト値
 テキスト値が必要です。

 テキストは、テンプレートに必要な .NET Framework の最小バージョン番号である必要があります。

## <a name="remarks"></a>Remarks

`RequiredFrameworkVersion` は、省略可能な要素です。 テンプレートには、特定の最小バージョン (およびそれ以降のバージョンが存在する場合) がサポートしている場合にのみ、この要素を使用して .NET Framework の。 指定した場合、`RequiredFrameworkVersion`要素と、テンプレートは、.NET Framework の特定の最小バージョンをサポートしない、**ターゲット フレームワーク バージョン**が適用されない場合、ドロップダウン リストが表示されます。

## <a name="example"></a>例

次の例では、標準のメタデータ[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]クラス テンプレートです。

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

この例では、テンプレートで必要とされる .NET Framework の最小バージョンで表される`RequiredFrameworkVersion`、3.0 です。 このテンプレートで作成したプロジェクトを対象に .NET Framework のバージョン 3.0 から開始できます。

## <a name="see-also"></a>関連項目

- [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
- [特定の .NET Framework バージョンをターゲットします。](../ide/targeting-a-specific-dotnet-framework-version.md)
