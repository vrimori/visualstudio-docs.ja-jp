---
title: MaxFrameworkVersion 要素 (Visual Studio テンプレート) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bc28fcc35a4a59852ef6864886acff4dc87ef60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 要素 (Visual Studio テンプレート)

テンプレートで必要とされる .NET Framework の最大バージョンを指定します。 使用可能な最大値を決定、**ターゲット フレームワークのバージョン**のドロップダウン リスト、**新しいプロジェクト**ダイアログ。 ユーザーが、framework のバージョンを選択できないためには、する必要がありますを指定するも[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)テンプレートに最低限の .NET Framework バージョンとして。

> [!IMPORTANT]
> Visual Studio 2017 15.6 のバージョンでの起動、**ターゲット フレームワークのバージョン**ドロップダウン リストが表示されているテンプレートのフィルターではなくなりました、**テンプレート**のセクションで、 **新しいプロジェクト**ダイアログ。 代わりに、**ターゲット フレームワークのバージョン**ドロップダウン リストが、選択したテンプレートのフレームワーク ピッカーとして機能します。

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

## <a name="syntax"></a>構文

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
```

## <a name="attributes-and-elements"></a>属性および要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性
 なし。

### <a name="child-elements"></a>子要素
 なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートをカテゴリに分類し、いずれかでの表示方法を定義、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|

## <a name="text-value"></a>テキスト値
 テキスト値が必要です。

 テキストは、テンプレートで許可されている .NET Framework の最新のバージョン番号があります。

## <a name="remarks"></a>コメント

`MaxFrameworkVersion` は、省略可能な要素です。 `MaxFrameworkVersion`要素は、テンプレートのサポートされているさまざまな .NET Framework のバージョンを誤って制限にならないように、必要である場合を除き、省略する必要があります。 また .NET Framework がテンプレートに適用されない場合も省略する必要があります。

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

この例では、テンプレートで必要とされる .NET Framework の最大バージョンによって表される`MaxFrameworkVersion`4.7.1 は、します。 このテンプレートで作成したプロジェクトは対象 4.7.1 までの .NET Framework のバージョンになります。

## <a name="see-also"></a>関連項目

- [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)
