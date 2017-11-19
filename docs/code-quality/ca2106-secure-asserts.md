---
title: "Ca 2106: セキュリティで保護されたアサート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 321d00f13ebc891070549778239fec60201d03c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2106-secure-asserts"></a>CA2106: アサートをセキュリティで保護します
|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 メソッドによってアクセス許可がアサートされますが、呼び出し元に対してセキュリティ チェックが実行されていません。  
  
## <a name="rule-description"></a>規則の説明  
 セキュリティ チェックを実行せずにセキュリティ アクセス許可をアサートすると、悪用される可能性があるセキュリティの弱点がコード内に残る場合があります。 セキュリティ アクセス許可がアサートされたときに、セキュリティのスタック ウォークが停止します。 呼び出し元に対してセキュリティ チェックを実行せずに、アクセス許可をアサートする場合、呼び出し元直接コードを実行されません、アクセス許可を使用します。 セキュリティ チェックは有害な方法で、アサートを使用できないことがわかっている場合のみで許容せずにアサートします。 呼び出すコードは、無害である場合は影響を与えません。 アサートを使用するか、ユーザーが任意の情報を呼び出すコードに渡すことはできません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、メソッド、またはその宣言型セキュリティの要求を追加します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 セキュリティを慎重確認した後のみ、この規則による警告を抑制します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)