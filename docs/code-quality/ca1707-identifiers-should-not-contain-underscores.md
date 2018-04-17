---
title: 'Ca 1707: 識別子はアンダー スコアを含むされません |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22c911f90e4da45ce847654f0c89455375ea478e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: 識別子はアンダースコアを含むことはできません
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|重大なアセンブリで発生したとき<br /><br /> 改行の型パラメーターで発生したとき|  
  
## <a name="cause"></a>原因  
 識別子の名前には、アンダー スコア (_) 文字が含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 名前付け規則では、識別子名にアンダースコア (_) 文字を含めることができません。 このルールは、名前空間、型、メンバー、およびパラメーターを確認します。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 名前からすべてのアンダー スコア文字を削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="related-rules"></a>関連規則  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)