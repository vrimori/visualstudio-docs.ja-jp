---
title: "Ca 2211: 非定数フィールドが表示されない |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac9a04038ba1d80e8abba2efbbab19c9779c384a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: 非定数フィールドは表示されません
|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクトの静的フィールドは定数ではありません。 または読み取り専用。  
  
## <a name="rule-description"></a>規則の説明  
 定数でも読み取り専用でもない静的フィールドは、スレッド セーフではありません。 このようなフィールドへのアクセスは、慎重に管理する必要があり、高度なプログラミング技法をクラス オブジェクトへのアクセスを同期する必要があります。 困難なスキルについては、これらは、マスター、およびテストするオブジェクトのような課題が独自ため、静的フィールドは変更されないデータの格納に適しています。 この規則の適用先ライブラリです。アプリケーションでは、フィールドを公開する必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、定数または読み取り専用、静的フィールドを設定します。 これが可能でない場合は、基になるフィールドへのスレッド セーフなアクセスを管理するスレッド セーフであるプロパティなどの代替手段を使用する型を設計し直します。 ロックの競合やデッドロックなどの問題は可能性があります、ライブラリの動作とパフォーマンスに影響することに注意してください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 アプリケーションを開発している場合は、この規則による警告を抑制して完全に制御を静的フィールドを含む型へのアクセスがあるために安全です。 ライブラリのデザイナーでは、この規則による警告は抑制しないでください。定数ではない静的フィールドを使用して適切に使用する開発者にとって困難ライブラリを使用してを行うことができます。  
  
## <a name="example"></a>例  
 次の例は、この規則に違反する型を示しています。  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]