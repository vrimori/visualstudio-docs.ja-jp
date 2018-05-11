---
title: 'CA1824: アセンブリを NeutralResourcesLanguageAttribute に設定します'
ms.date: 03/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: beaef23dd5b3047d1d65b90fdd984dfdedd7e145
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: アセンブリを NeutralResourcesLanguageAttribute に設定します

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

アセンブリに含まれる、 **ResX**-リソースのベースがありません、<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>を適用します。

## <a name="rule-description"></a>規則の説明

<xref:System.Resources.NeutralResourcesLanguageAttribute>属性は、アプリの既定のカルチャのリソース マネージャーを通知します。 既定のカルチャのリソースがアプリのメインのアセンブリに埋め込まれている場合と<xref:System.Resources.ResourceManager>既定のカルチャと同じカルチャに属しているリソースを取得するが、<xref:System.Resources.ResourceManager>メイン アセンブリにあるリソースを自動的に使用サテライト アセンブリを検索して代わりにはいます。 これにより、通常のアセンブリのプローブをバイパスする、読み込んで、ワーキング セットを減らすことができますの最初のリソースに対する検索のパフォーマンスが向上します。

> [!TIP]
> 参照してください[パッケージ化とリソースを配置](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps)プロセスを<xref:System.Resources.ResourceManager>リソース ファイルを探すために使用します。

## <a name="fix-violations"></a>違反を修正します。

この規則違反を修正するには、アセンブリに属性を追加し、ニュートラル カルチャのリソースの言語を指定します。

### <a name="to-specify-the-neutral-language-for-resources"></a>ニュートラル言語リソースを指定するには

1. **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、**プロパティ**です。

2. 選択、**アプリケーション**、タブをクリックし**アセンブリ情報**です。

   > [!NOTE]
   > プロジェクトが .NET 標準または .NET Core プロジェクトの場合は、選択、**パッケージ**タブです。

3. 言語を選択して、**ニュートラル言語**または**アセンブリのニュートラル言語**ドロップダウン リスト。

4. **[OK]** を選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告を抑制することはできます。 ただし、起動時のパフォーマンスが低下する可能性があります。

## <a name="see-also"></a>関連項目

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [デスクトップ アプリケーション (.NET) でのリソース](/dotnet/framework/resources/)
- [Ca 1703 - リソース文字列正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [Ca 1701 - リソースの文字列の複合語では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)