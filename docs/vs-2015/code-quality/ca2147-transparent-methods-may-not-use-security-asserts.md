---
title: 'CA2147: 透過的メソッドに次のセキュリティを使用してはいないアサート |Microsoft Docs'
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
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6542a2063d076cb57750015039f413b2faf4bca4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921640"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: 透過コードは、セキュリティ アサートを使用してはならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コードとしてマークされている<xref:System.Security.SecurityTransparentAttribute>をアサートするための十分なアクセス許可が付与されていません。

## <a name="rule-description"></a>規則の説明
 このルールで、すべてのメソッドとのすべての宣言型または命令型の使用フラグを設定され、100% 透明または混合透過的/クリティカル、アセンブリ内の型を分析<xref:System.Security.CodeAccessPermission.Assert%2A>します。

 実行時に、すべての呼び出しに<xref:System.Security.CodeAccessPermission.Assert%2A>transparent コードから発生、<xref:System.InvalidOperationException>がスローされます。 これは、両方の 100% 透過的なアセンブリと透過的/クリティカルの混在のアセンブリ、メソッドまたは型が透過的な場合は、宣言されているが、宣言的または強制的 Assert が含まれていますに発生することができます。

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 という機能が導入*透明度*します。 個々 のメソッド、フィールド、インターフェイス、クラス、および種類は、transparent または重要なのかを指定できます。

 透過的なコードは、セキュリティ特権の昇格は許可されません。 そのため、許可または要求されるアクセス許可は自動的にコードに渡さ呼び出し元またはホスト アプリケーション ドメイン。 昇格の例には、アサート、LinkDemands、SuppressUnmanagedCode、および`unsafe`コード。

## <a name="how-to-fix-violations"></a>違反の修正方法
 問題を解決するには、マークのアサートを呼び出したコード、 <xref:System.Security.SecurityCriticalAttribute>、または削除、アサートします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールからのメッセージを抑制しないでください。

## <a name="example"></a>例
 このコードは失敗`SecurityTestClass`がときに透明で、`Assert`メソッドがスローされます、<xref:System.InvalidOperationException>します。

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>例
 コード レビュー方法メソッドは、次の例で 1 つのオプションがあり、メソッドが昇格に対して安全と見なされると、マークの方法でセキュリティ保護に不可欠なこのことが必要詳細、完了すると、およびエラーのないセキュリティ監査は、アサート対象のメソッド内で発生するすべての呼び出し-アウトと共にメソッドには実行する必要があります。

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 コードから、アサートを削除し、その後、ファイル、呼び出し元に方法を超える I/O アクセス許可の要求フローを使用する別の方法です。 これにより、セキュリティ チェックができます。 この場合、セキュリティ監査は通常必要ありません、ため、アクセス許可の要求は、呼び出し元や、アプリケーション ドメインにフローします。 アクセス許可の要求は、環境、およびソース コードのアクセス許可の付与をホストしている、セキュリティ ポリシーを通じて密接に制御されます。

## <a name="see-also"></a>関連項目
 [セキュリティの警告](../code-quality/security-warnings.md)



