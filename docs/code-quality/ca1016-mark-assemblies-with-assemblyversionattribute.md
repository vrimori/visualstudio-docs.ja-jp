---
title: 'CA1016: アセンブリに AssemblyVersionAttribute を設定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3a6ccdc84a2db30aab2352d65bd716936cb522e6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547595"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: アセンブリに AssemblyVersionAttribute を設定します

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

アセンブリのバージョン番号ではありません。

## <a name="rule-description"></a>規則の説明

アセンブリの id は、次の情報で構成されます。

- [アセンブリ名]

- バージョン番号

- culture

- (厳密な名前付きアセンブリの場合) の公開キー。

[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] では、バージョン番号を使用してアセンブリを一意に識別し、厳密な名前を持つアセンブリの型にバインドします。 バージョン番号は、バージョンと発行者のポリシーと共に使用されます。 既定で、アプリケーションは、ビルドされたアセンブリのバージョンでのみ実行されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するを使用して、アセンブリにバージョン番号を追加します。、<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>属性。 次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 サード パーティがまたは運用環境で使用されているアセンブリは、この規則による警告を抑制しないでください。

## <a name="example"></a>例
 次の例では、アセンブリが、<xref:System.Reflection.AssemblyVersionAttribute>属性が適用されています。

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>関連項目

- [アセンブリのバージョン管理](/dotnet/framework/app-domains/assembly-versioning)
- [方法: 発行者ポリシーを作成する](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)