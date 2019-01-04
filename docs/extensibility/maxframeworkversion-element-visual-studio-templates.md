---
title: MaxFrameworkVersion 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e28364360cf636273384480a35cd07468b9b7e6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845578"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 要素 (Visual Studio テンプレート)

テンプレートで必要とされる .NET Framework の最大バージョンを指定します。 使用可能な最大値を決定、**ターゲット フレームワークのバージョン**のドロップダウン リスト、**新しいプロジェクト**ダイアログ。 ユーザーのバージョンのフレームワークを選択できるようにするためには、する必要がありますを指定するも[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)テンプレートについては、.NET Framework の最小バージョンとして。

> [!IMPORTANT]
> Visual Studio 2017 バージョン 15.6 では、以降、**ターゲット フレームワーク バージョン**ドロップダウンが表示されているテンプレートのフィルターでは不要になった、**テンプレート**のセクション、 **の新しいプロジェクト**ダイアログ。 代わりに、**ターゲット フレームワーク バージョン**ドロップダウンが選択したテンプレートの framework ピッカーとして機能します。

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

## <a name="syntax"></a>構文

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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

 テキストは、テンプレートで許可されている .NET Framework の最上位のバージョン番号である必要があります。

## <a name="remarks"></a>Remarks

`MaxFrameworkVersion` は、省略可能な要素です。 `MaxFrameworkVersion`テンプレートについては、.NET Framework のサポートされているバージョンを誤って制限にならないように、必要な場合を除き、要素を省略する必要があります。 また .NET Framework がテンプレートに適用されない場合も省略する必要があります。

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

この例では、テンプレートで必要とされる .NET Framework の最大バージョンで表される`MaxFrameworkVersion`4.7.1 は、します。 このテンプレートで作成されたプロジェクト バージョンの .NET Framework 4.7.1 まで対象にできます。

## <a name="see-also"></a>関連項目

- [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)
