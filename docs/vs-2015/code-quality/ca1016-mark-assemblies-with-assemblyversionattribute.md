---
title: 'Ca 1016: マーク アセンブリに assemblyversionattribute を設定します |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bd572cfff52537eab58e06ddf8f7a34bb087513c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305384"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: アセンブリに AssemblyVersionAttribute を設定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

-   [アセンブリ名]

-   バージョン番号

-   culture

-   (厳密な名前付きアセンブリの場合) の公開キー。

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] では、バージョン番号を使用してアセンブリを一意に識別し、厳密な名前を持つアセンブリの型にバインドします。 バージョン番号は、バージョンと発行者のポリシーと共に使用されます。 既定で、アプリケーションは、ビルドされたアセンブリのバージョンでのみ実行されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するを使用して、アセンブリにバージョン番号を追加します。、<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>属性。 次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 サード パーティがまたは運用環境で使用されているアセンブリは、この規則による警告を抑制しないでください。

## <a name="example"></a>例
 次の例では、アセンブリが、<xref:System.Reflection.AssemblyVersionAttribute>属性が適用されています。

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>関連項目
 [アセンブリのバージョン管理](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)[方法: 発行者ポリシーを作成](http://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)



