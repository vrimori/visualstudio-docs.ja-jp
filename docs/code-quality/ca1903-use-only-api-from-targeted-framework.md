---
title: 'CA1903: 対象のフレームワークから API のみを使用して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b61f1281c88404d3331d9a94d5767a9052786700
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: 対象のフレームワークから API のみを使用します
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|カテゴリ|Microsoft.Portability|  
|互換性に影響する変更点|互換性に影響するのに対して、外部から参照できるメンバーまたは型のシグネチャが発生したとき。<br /><br /> なし - のメソッドの本体で発生したときにします。|  
  
## <a name="cause"></a>原因  
 メンバーまたはプロジェクトの対象となるフレームワークに含まれていない service pack で導入された型、メンバーまたは型を使用します。  
  
## <a name="rule-description"></a>規則の説明  
 新しいメンバーと型は、.NET Framework 2.0 Service Pack 1 および 2、.NET Framework 3.0 Service Pack 1 および 2、および .NET Framework 3.5 Service Pack 1 で追加されました。 .NET Framework のメジャー バージョンを対象とするプロジェクトは、新しい Api でこれらの依存関係を意図せず実行できます。 この依存関係を防ぐためには、この規則は、任意の新しいメンバーと既定では、プロジェクトのターゲット フレームワークに含まれていない型の使用に適用されます。  
  
 **ターゲット フレームワークおよびサービス パックの依存関係**  
  
|||  
|-|-|  
|ターゲット フレームワーク|導入されたメンバーの使用状況の発生|  
|.NET Framework 2.0|.NET framework 2.0 SP1 では、.NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N/A|  
  
 プロジェクトのターゲット フレームワークを変更するを参照してください。[特定の .NET Framework のバージョンを対象とする](../ide/targeting-a-specific-dotnet-framework-version.md)です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 サービス パックへの依存関係を削除するには、新しいメンバーまたは型のすべての使用状況を削除します。 これが意図的な依存関係である場合は、警告を抑制するか、このルールをオフにします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 これが、指定したサービス パックに依存関係が意図的でない場合は、この規則による警告は抑制しないでください。 この場合、この service pack がインストールされていないシステムで実行するアプリケーションが失敗します。 警告を抑制または意図的な依存関係の場合、このルールを無効にします。  
  
## <a name="example"></a>例  
 次の例では、型は .NET 2.0 Service Pack 1 でのみ使用 DateTimeOffset を使用するクラスを示します。 この例では、.NET Framework 2.0 がプロジェクトのプロパティでターゲット フレームワーク ドロップダウン リストで選択されている必要があります。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、DateTime 型を持つ DateTimeOffset 型の使用状況を置き換えることで、既に説明した違反を修正します。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 [移植性に関する警告](../code-quality/portability-warnings.md)   
 [対象となる特定の .NET Framework バージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)