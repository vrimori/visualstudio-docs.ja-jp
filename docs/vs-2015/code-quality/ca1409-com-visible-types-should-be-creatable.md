---
title: 'Ca 1409: Com 参照可能な型は、可能でなければなりません。Microsoft Docs'
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
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8d6a28acea085fad99549739a0c4ab132169a436
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889779"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: COM 参照可能な型は作成可能でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている参照型では、パブリックのパラメーター化されたコンス トラクターが含まれていますが、(パラメーターなしの) パブリックの既定のコンス トラクターが含まれていません。

## <a name="rule-description"></a>規則の説明
 COM クライアントでは、パブリックの既定のコンス トラクターのない型を作成できません。 ただし、種類もアクセスできます COM クライアントで別の手段の種類を作成し (たとえば、メソッド呼び出しの戻り値) を使用してクライアントに渡すことがある場合。

 派生した型を規則<xref:System.Delegate?displayProperty=fullName>します。

 既定では、次は COM から参照できる: アセンブリ、型のパブリック、パブリック型は、パブリック インスタンス メンバーおよびパブリック値型のすべてのメンバー。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、既定のパブリック コンス トラクターを追加または削除、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>型から。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 COM クライアントを作成し、オブジェクトを他の方法が提供されている場合は、この規則による警告を抑制するのには安全です。

## <a name="related-rules"></a>関連規則
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目
 [相互運用のための .NET 型を修飾](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)[アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



