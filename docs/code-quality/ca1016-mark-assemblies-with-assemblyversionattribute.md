---
title: 'Ca 1016: マーク アセンブリに assemblyversionattribute を設定します |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: 9dc5bea6f18265117c0d284ed048009ff9fdafcd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
-   [アセンブリ名]  
  
-   バージョン番号  
  
-   culture  
  
-   公開キー (厳密な名前付きアセンブリの場合)。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] では、バージョン番号を使用してアセンブリを一意に識別し、厳密な名前を持つアセンブリの型にバインドします。 バージョン番号は、バージョンと発行者のポリシーと共に使用されます。 既定で、アプリケーションは、ビルドされたアセンブリのバージョンでのみ実行されます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するを使用して、アセンブリにバージョン番号を追加します。、<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>属性。 次の例を参照してください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 サード パーティや実稼働環境で使用するアセンブリには、この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、アセンブリが、<xref:System.Reflection.AssemblyVersionAttribute>属性を適用します。  
  
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## <a name="see-also"></a>関連項目  
 [アセンブリのバージョン管理](/dotnet/framework/app-domains/assembly-versioning)   
 [方法: 発行者ポリシーを作成する](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)