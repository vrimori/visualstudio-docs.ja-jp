---
title: "CA2132: 既定のコンス トラクターは、少なくとも基本データ型の既定のコンス トラクターとしてほど重要である必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 752103825a25c4352ccc21730b8d2b7265f8f41b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: 既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要
|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
> [!NOTE]
>  この警告は、CoreCLR (Silverlight Web アプリケーションに固有である CLR のバージョン) を実行しているコードにのみ適用されます。  
  
## <a name="cause"></a>原因  
 派生クラスの既定のコンス トラクターの透過性属性が基底クラスの透明度ほど重要ではありません。  
  
## <a name="rule-description"></a>規則の説明  
 型およびメンバーを持つ、 <xref:System.Security.SecurityCriticalAttribute> Silverlight アプリケーション コードで使用することはできません。 セキュリティが重要な型やメンバーは、.NET Framework for Silverlight クラス ライブラリの信頼されているコードからのみ使用できます。 派生クラスにおけるパブリックな構築または保護された構築の透過性は、基底クラスと同程度以上である必要があるため、アプリケーション内のクラスを、SecurityCritical としてマークされたクラスから派生させることはできません。  
  
 CoreCLR プラットフォーム コードでは、基本データ型は、public または protected の非透過の既定のコンス トラクターを持つ場合、派生型従う必要があります既定コンス トラクターの継承規則。 派生型は既定のコンス トラクターにも必要し、そのコンス トラクターが、基本型の重要な既定のコンス トラクターとして以上である必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 違反を修正するには、型を削除するか、セキュリティ透過的でない型から派生していません。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。 CoreCLR で型の読み込みを拒否しているアプリケーション コードでは、この規則の違反が発生、<xref:System.TypeLoadException>です。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### <a name="comments"></a>コメント