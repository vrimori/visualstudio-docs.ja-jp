---
title: 'Ca 1410: COM 登録メソッドは一致する必要があります |Microsoft Docs'
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
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 228c5faffc2cf3ceb48cc8c88c6cefa88f63b2cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273625"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: COM 登録メソッドは一致しなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 マークされているメソッドを宣言する型、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>属性しますが、でマークされているメソッドを宣言しません、<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性、またはその逆です。

## <a name="rule-description"></a>規則の説明
 コンポーネント オブジェクト モデル (COM) クライアントを作成する、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]型、型を登録することが最初にする必要があります。 可能な場合でマークされているメソッド、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>属性は、ユーザー指定のコードを実行する登録プロセス中に呼び出されます。 マークされている対応するメソッド、<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>属性は、登録メソッドの操作を反転する登録解除プロセス中に呼び出されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、対応する登録または登録解除メソッドを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。 コメント付きのコードでは、違反の修正プログラムを示します。

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1411: COM 登録メソッドは参照可能であることはできません](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [COM にアセンブリを登録する](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (アセンブリ登録ツール)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)



