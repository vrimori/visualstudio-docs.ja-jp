---
title: ': Ca 1040 空のインターフェイス |Microsoft Docs'
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
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 59951f1c8bb0e3b2573880beb5350e63b8570710
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855085"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: 空のインターフェイスは使用しないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 インターフェイスのメンバーの宣言または他の 2 つ以上のインターフェイスの実装はできません。

## <a name="rule-description"></a>規則の説明
 インターフェイスには、動作や使用のコントラクトを実現するメンバーが定義されます。 インターフェイスで示される機能は、継承の階層構造内に型が存在するかどうかにかかわらず、どの型からも適用できます。 型ではインターフェイスのメンバーに実装することで、インターフェイスが実装されます。 空のインターフェイスでは、すべてのメンバーは定義しません。 そのため、実装できるコントラクトは定義しません。

 空のデザインが含まれている場合、型インターフェイスの実装が期待される、マーカーまたは型のグループを識別する方法として、インターフェイスを使用している可能性があります。 この id は実行時に発生した場合、これを実現する正しい方法は、カスタム属性を使用します。 対象の種類を識別するために存在するか、属性がない場合や、属性のプロパティを使用します。 Id は、空のインターフェイスを使用することができますし、コンパイル時に行う必要があります。 場合、

## <a name="how-to-fix-violations"></a>違反の修正方法
 インターフェイスを削除するか、メンバーを追加します。 空のインターフェイスは、型のセットのラベル付けに使用されているが場合、は、カスタム属性を持つインターフェイスを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 コンパイル時に一連の型を識別するために、インターフェイスを使用する場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、空のインターフェイスを示します。

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]



