---
title: "Ca 1409: Com 参照可能な型を作成可能にする必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f12dda380f887aca50b764d0ec20f9db1c0cd07c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: COM 参照可能な型は作成可能でなければなりません
|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|カテゴリ|Microsoft.Interoperability|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている参照型では、パブリックのパラメーター化されたコンス トラクターが含まれていますが、パブリックの既定 (パラメーターなし) コンス トラクターが含まれていません。  
  
## <a name="rule-description"></a>規則の説明  
 COM クライアントで既定のパブリック コンス トラクターのない型を作成できません。 ただし、型もアクセスできます COM クライアントで別の方法がある型を作成し、(たとえば、メソッド呼び出しの戻り値) を使用してクライアントに渡す場合。  
  
 この規則から派生した<xref:System.Delegate?displayProperty=fullName>です。  
  
 既定では、次が COM 参照可能な: アセンブリ、パブリックな型、パブリック型は、パブリック インスタンス メンバーおよびパブリック値型のすべてのメンバーです。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、既定のパブリック コンス トラクターを追加または削除、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>型からです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 作成し、COM クライアントにオブジェクトを渡す他の方法が用意されている場合、この規則による警告を抑制しても安全であります。  
  
## <a name="related-rules"></a>関連規則  
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>参照  
 [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)