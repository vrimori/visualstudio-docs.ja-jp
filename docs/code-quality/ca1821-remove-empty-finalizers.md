---
title: 'Ca 1821: 空のファイナライザーを削除する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75c77a35fc09ea4b45bdbef756341b330bdd11df
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: 空のファイナライザーを削除します
|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|カテゴリ|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 型では、空では、基本型のファイナライザーを呼び出す、または条件付きで出力されたメソッドのみを呼び出しているファイナライザーを実装します。  
  
## <a name="rule-description"></a>規則の説明  
 オブジェクトの有効期間の追跡に関連するパフォーマンス オーバーヘッドが増大するため、ファイナライザーは可能な限り使用しないでください。 オブジェクトを収集する前に、ガベージ コレクターは、ファイナライザーを実行します。 これは、2 つのコレクションをオブジェクトを収集するために必要になることを意味します。 空のファイナライザーでは、この何の利点も追加のオーバーヘッドが生じます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 空のファイナライザーを削除します。 ファイナライザーがデバッグに必要な場合は、全体のファイナライザーを囲みます`#if DEBUG / #endif`ディレクティブです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則からのメッセージを抑制しないでください。 エラーを抑制する状況終了処理は、パフォーマンスが低下しも利点です。  
  
## <a name="example"></a>例  
 次の例は、空のファイナライザーを削除するかで囲む必要がありますが、不要なファイナライザー`#if DEBUG / #endif`ディレクティブ、およびファイナライザーを使用する、`#if DEBUG / #endif`ディレクティブ正しくです。  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]