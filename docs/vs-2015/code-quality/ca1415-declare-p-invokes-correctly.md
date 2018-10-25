---
title: '1415: ca P/invoke は正しく宣言 |Microsoft Docs'
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
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2a945029652f67fe7332a336e62523bba8175f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857290"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invoke を正しく宣言します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|非的な P/invoke パラメーターを宣言する場合は、アセンブリの外部表示できません。 あり - 場合は、アセンブリの外部パラメーターを宣言する P/invoke を確認できます。|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメソッド宣言が正しくありません。

## <a name="rule-description"></a>規則の説明
 プラットフォームがメソッドへのアクセスのアンマネージ コードを呼び出すし、によって定義されている、`Declare`キーワード[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]または<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>します。 現時点では、このルールは、プラットフォーム呼び出しメソッドの宣言を OVERLAPPED 構造体パラメーターへのポインターを持つ Win32 関数を対象とすると、対応するマネージ型のパラメーターがないへのポインターを検索、<xref:System.Threading.NativeOverlapped?displayProperty=fullName>構造体。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、プラットフォームを正しく宣言メソッドを呼び出します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例はプラットフォームが、規則に違反して、規則に適合するメソッドを呼び出します。

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>関連項目
 [アンマネージ コードとの相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



