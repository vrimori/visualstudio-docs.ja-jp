---
title: 'CA2147: 透過的メソッドに次のセキュリティを使用してはいないアサート |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75d841da0c738ff7504e95b372ecd4e06f9c77f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: 透過コードは、セキュリティ アサートを使用してはならない
|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 としてマークされているコード<xref:System.Security.SecurityTransparentAttribute>をアサートするための十分なアクセス許可が付与されません。  
  
## <a name="rule-description"></a>規則の説明  
 このルールですべてのメソッドとは、100% 透過的または混合透過的/クリティカル、および宣言的または強制的使用されているフラグを設定するアセンブリ内の型を分析<xref:System.Security.CodeAccessPermission.Assert%2A>です。  
  
 実行時への呼び出しの<xref:System.Security.CodeAccessPermission.Assert%2A>透過的なコードからなる、<xref:System.InvalidOperationException>がスローされます。 これは、両方の 100% 透過的なアセンブリと透過的/クリティカルの混在のアセンブリ、メソッドまたは型が透過的で宣言されているが、宣言的または強制的アサートが含まれていますに発生することができます。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 という機能が導入*透過性*です。 個々 のメソッド、フィールド、インターフェイス、クラス、および型は、透過的なまたは重要なのかを指定できます。  
  
 透過的なコードは、セキュリティ特権の昇格は許可されません。 そのため、許可または要求されるアクセス許可は自動的にコードに渡さ、呼び出し元またはホストのアプリケーション ドメイン。 昇格の例については、アサート、LinkDemands、SuppressUnmanagedCode、および`unsafe`コード。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 問題を解決するには、いずれかのマークを付けると、アサートを呼び出したコード、 <xref:System.Security.SecurityCriticalAttribute>、またはアサートを削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則からのメッセージを抑制しないでください。  
  
## <a name="example"></a>例  
 このコードは失敗`SecurityTestClass`ときは透過的で、`Assert`メソッドがスローされます、<xref:System.InvalidOperationException>です。  
  
 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## <a name="example"></a>例  
 コード レビュー方法メソッドで次の例では、1 つのオプションとメソッドが昇格に対して安全と見なされると、マークの方法で重要セキュリティで保護する必要が詳細な完全、およびエラーのないセキュリティ監査は、すべてコールアウト アサート対象のメソッド内で発生すると、メソッドで実行する必要があります。  
  
 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 コードからアサートを削除して、その後、ファイル方法以外の I/O のアクセス許可要求フロー、呼び出し元にすることもできます。 これにより、セキュリティ チェックできます。 この場合、セキュリティ監査は通常不要、アクセス許可要求は、呼び出し元や、アプリケーション ドメインにフローするためです。 アクセス許可の要求は、環境、およびソース コードのアクセス許可の付与をホストしているセキュリティ ポリシーによって厳密に制御されます。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティの警告](../code-quality/security-warnings.md)