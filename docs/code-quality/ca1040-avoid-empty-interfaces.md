---
title: ": Ca 1040 空のインターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1b2dd61f70328ed4aa8ca08c518cebf8d6abbedb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: 空のインターフェイスは使用しないでください
|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 インターフェイスのメンバーの宣言またはその他の 2 つ以上のインターフェイスを実装はできません。  
  
## <a name="rule-description"></a>規則の説明  
 インターフェイスには、動作や使用のコントラクトを実現するメンバーが定義されます。 インターフェイスで示される機能は、継承の階層構造内に型が存在するかどうかにかかわらず、どの型からも適用できます。 型ではインターフェイスのメンバーに実装することで、インターフェイスが実装されます。 空のインターフェイスでは、すべてのメンバーは定義しません。 したがって、実装できるコントラクトは定義しません。  
  
 デザインに空白を含める場合は、型のインターフェイスの実装が期待される、マーカーまたはの種類のグループを識別する方法として、インターフェイスを使用している可能性があります。 この id は、実行時に発生する可能性は、これを実現するための正しい方法は、カスタム属性を使用するです。 存在するか、属性がない場合や、属性のプロパティを使用して、対象の種類を識別します。 Id は、空のインターフェイスを使用することができますし、コンパイル時に行う必要がある場合。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 インターフェイスを削除するか、メンバーを追加します。 空のインターフェイスが、一連の型のラベル付けに使用される場合は、カスタム属性を持つインターフェイスを置き換えます。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 インターフェイスを使用して、コンパイル時に一連の型を識別するこの規則による警告を抑制しても安全です。  
  
## <a name="example"></a>例  
 次の例では、空のインターフェイスを示します。  
  
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]