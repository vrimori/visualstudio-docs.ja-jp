---
title: ": Ca 1407 COM 参照可能な型で静的メンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9cb2b7a95772ddd95bf4379ea0749cf42419a182
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Com 参照可能な型で静的メンバーを使用しません
|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|カテゴリ|Microsoft.Interoperability|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている型に含まれる、`public``static`メソッドです。  
  
## <a name="rule-description"></a>規則の説明  
 COM をサポートしません`static`メソッドです。  
  
 このルールは、プロパティおよびイベント アクセサー、演算子のメソッド、またはいずれかを使用してマークされているメソッドをオーバー ロードは無視されます、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>属性または<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性。  
  
 既定では、次が COM 参照可能な: アセンブリ、パブリックな型、パブリック型は、パブリック インスタンス メンバーおよびパブリック値型のすべてのメンバーです。  
  
 このルールで発生すると、アセンブリ レベルの<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定する必要があります`false`およびクラスの<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定する必要があります`true`次のコードに示すようにします。  
  
```csharp  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正すると同じ機能を提供するインスタンス メソッドを使用してデザインを変更、`static`メソッドです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 COM クライアントに用意されている機能へのアクセスが必要としない場合は、この規則による警告を抑制するのには安全では、`static`メソッドです。  
  
## <a name="example-violation"></a>違反の例  
  
### <a name="description"></a>説明  
 次の例は、`static`この規則に違反するメソッド。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### <a name="comments"></a>コメント  
 この例では、 **Book.FromPages** COM からメソッドを呼び出すことができません  
  
## <a name="example-fix"></a>例の修正プログラム  
  
### <a name="description"></a>説明  
 前の例で、違反を修正するインスタンス メソッドをメソッドに変更できますをなさないがこのインスタンスでします。 優れたソリューションを明示的に適用する`ComVisible(false)`他の開発者が COM からメソッドを表示できないことをチェック ボックスをオフにするメソッド  
  
 次の例では適用<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>メソッドにします。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## <a name="see-also"></a>参照  
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)