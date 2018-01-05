---
title: "Ca 1032: 標準例外コンス トラクターを実装して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 640aacaf67ba20e801ac9657aeff20b091c5032e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: 標準例外コンストラクターを実装します
|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 型拡張<xref:System.Exception?displayProperty=fullName>し、必要なすべてのコンス トラクターを宣言しません。  
  
## <a name="rule-description"></a>規則の説明  
 例外の種類は、次のコンス トラクターを実装する必要があります。  
  
-   パブリック NewException()  
  
-   パブリック NewException(string)  
  
-   パブリック NewException (string, 例外)  
  
-   保護されているかプライベート NewException (SerializationInfo、StreamingContext)  
  
 コンストラクターを完全に宣言していないと、例外を正しく処理するのが困難になります。 たとえば、コンス トラクターは、シグネチャを持つ`NewException(string, Exception)`他の例外によって引き起こされる例外を作成するために使用します。 このコンス トラクターがない作成して、カスタムの例外を内部の (入れ子になった) 例外を含むインスタンスをスローすることはできません、どのようなマネージ コードは、このような状況で行う必要がありますはします。 最初の 3 つの例外のコンス トラクターは、規約によってパブリックです。 4 番目のコンス トラクターは、封印されていないクラスで保護されているシール クラスではプライベートです。 詳細については、次を参照してください[ca 2229: シリアル化コンス トラクターを実装する。](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、例外に必要なコンス トラクターを追加し、適切なアクセシビリティであるかどうかを確認します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 パブリック コンス トラクターを異なるアクセス レベルを使用して、違反が発生する場合は、この規則による警告を抑制するのには安全です。  
  
## <a name="example"></a>例  
 次の例には、この規則に違反する例外の種類と正しく実装されている例外の種類が含まれています。  
  
 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]