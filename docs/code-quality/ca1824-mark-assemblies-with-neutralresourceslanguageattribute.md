---
title: CA1824:アセンブリを NeutralResourcesLanguageAttribute に設定します
ms.date: 03/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db780257c83c42f97500a83f1843332cae0ecea3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825177"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824:アセンブリを NeutralResourcesLanguageAttribute に設定します

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

アセンブリに含まれる、 **ResX**-ベースのリソースがありません、<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>を適用します。

## <a name="rule-description"></a>規則の説明

<xref:System.Resources.NeutralResourcesLanguageAttribute>属性が、アプリの既定のカルチャのリソース マネージャーに通知します。 既定のカルチャのリソースが、アプリのメイン アセンブリに埋め込まれている場合と<xref:System.Resources.ResourceManager>既定のカルチャと同じカルチャに属しているリソースを取得する必要があります、<xref:System.Resources.ResourceManager>メイン アセンブリに配置されているリソースを自動的に使用されます代わりに、サテライト アセンブリを検索しています。 これは、通常のアセンブリのプローブをバイパスする、最初のリソースを読み込み、および、ワーキング セットを減らすことができますのルックアップのパフォーマンスが向上します。

> [!TIP]
> 参照してください[パッケージ化とリソースのデプロイ](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps)プロセスを<xref:System.Resources.ResourceManager>リソース ファイルを探すために使用します。

## <a name="fix-violations"></a>違反を修正します。

この規則違反を修正するには、アセンブリに属性を追加し、ニュートラル カルチャのリソースの言語を指定します。

### <a name="to-specify-the-neutral-language-for-resources"></a>ニュートラル言語リソースを指定するには

1. **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、**プロパティ**します。

2. 選択、**アプリケーション**、タブを選び**アセンブリ情報**します。

   > [!NOTE]
   > プロジェクトが .NET Standard または .NET Core プロジェクトの場合は、選択、**パッケージ**タブ。

3. 言語を選択して、**ニュートラル言語**または**アセンブリのニュートラル言語**ドロップダウン リスト。

4. **[OK]** を選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告を抑制することはできます。 ただし、起動時のパフォーマンスが低下する可能性があります。

## <a name="see-also"></a>関連項目

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [デスクトップ アプリ (.NET) でのリソース](/dotnet/framework/resources/)
- [Ca 1703 - リソース文字列正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 - リソース文字列の複合語では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)