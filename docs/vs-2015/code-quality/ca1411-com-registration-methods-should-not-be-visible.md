---
title: '1411: ca COM 登録メソッドできません表示 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 410531222f19632f6358bdbc320b95fe1254bafe
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589776"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: COM 登録メソッドは参照可能であることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1411: COM 登録メソッドが表示されない](https://docs.microsoft.com/visualstudio/code-quality/ca1411-com-registration-methods-should-not-be-visible)します。

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 マークされているメソッド、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性は、外部から参照します。

## <a name="rule-description"></a>規則の説明
 アセンブリ コンポーネント オブジェクト モデル (COM) で登録されると、アセンブリで COM から参照できる各型のレジストリにエントリが追加されます。 マークされているメソッド、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>と<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>属性中に呼び出される登録および登録解除プロセスでは、それぞれに、これらの型の登録または登録解除に固有のユーザー コードを実行します。 このコードは、これらのプロセス外呼び出されませんする必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、メソッドのアクセシビリティを変更`private`または`internal`(`Friend`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールに違反している 2 つの方法を示します。

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1410: COM 登録メソッドは一致しなければなりません](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [COM にアセンブリを登録する](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (アセンブリ登録ツール)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)



