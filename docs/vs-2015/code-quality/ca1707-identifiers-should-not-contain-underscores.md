---
title: 'Ca 1707: 識別子はアンダー スコアを含むされません |Microsoft Docs'
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
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c34b03e57d1b303ba6a5f782fd5a5de5afe81ad0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547939"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: 識別子はアンダースコアを含むことはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。 [ca 1707: 識別子はアンダー スコアを含めることはできません](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores)docs.microsoft.com でリリースされました。  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|重大なアセンブリで発生したときに<br /><br /> 非的な型パラメーターで発生したときに|  
  
## <a name="cause"></a>原因  
 識別子の名前にアンダー スコア (_) 文字が含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 名前付け規則では、識別子名にアンダースコア (_) 文字を含めることができません。 このルールは、名前空間、型、メンバー、およびパラメーターを確認します。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 名前からは、すべてのアンダー スコア文字を削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="related-rules"></a>関連規則  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

