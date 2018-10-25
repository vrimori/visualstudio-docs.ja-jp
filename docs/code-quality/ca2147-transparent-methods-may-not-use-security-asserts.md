---
title: 'CA2147: 透過コードは、セキュリティ アサートを使用してはならない'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: 3f701a0e39124327c897043590b318cb6e645c1f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923798"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: 透過コードは、セキュリティ アサートを使用してはならない

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コードとしてマークされている<xref:System.Security.SecurityTransparentAttribute>をアサートするための十分なアクセス許可が付与されていません。

## <a name="rule-description"></a>規則の説明
 このルールで、すべてのメソッドとか 100% 透明または混合透過的/クリティカルは、宣言型または命令型の使用量のフラグを設定するアセンブリ内の型を分析<xref:System.Security.CodeAccessPermission.Assert%2A>します。

 実行時に、すべての呼び出しに<xref:System.Security.CodeAccessPermission.Assert%2A>transparent コードから発生、<xref:System.InvalidOperationException>がスローされます。 これは、両方の 100% 透過的なアセンブリと透過的/クリティカルの混在のアセンブリ、メソッドまたは型が透過的な場合は、宣言されているが、宣言的または強制的 Assert が含まれていますに発生することができます。

 .NET Framework 2.0 には、という名前の機能が導入されました。*透明度*します。 個々 のメソッド、フィールド、インターフェイス、クラス、および種類は、transparent または重要なのかを指定できます。

 透過的なコードは、セキュリティ特権の昇格は許可されません。 そのため、許可または要求されるアクセス許可は自動的にコードに渡さ呼び出し元またはホスト アプリケーション ドメイン。 昇格の例には、アサート、LinkDemands、SuppressUnmanagedCode、および`unsafe`コード。

## <a name="how-to-fix-violations"></a>違反の修正方法
 コードを呼び出すと、アサートをマークする問題を解決するには、いずれか、 <xref:System.Security.SecurityCriticalAttribute>、または削除、アサートします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 このルールからのメッセージを抑制しないでください。

## <a name="example"></a>例
 このコードは失敗`SecurityTestClass`がときに透明で、`Assert`メソッドがスローされます、<xref:System.InvalidOperationException>します。

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>例
 1 つのオプションは、コード レビュー方法メソッドは、次の例ではし、メソッドは、昇格の安全と見なされますが場合、は、セキュリティで保護された重要なの方法をマークします。 これは、アサート対象のメソッド内で発生するすべての呼び出し-アウトと共にメソッドの詳細、完了すると、およびエラーのないセキュリティ監査を実行することが必要です。

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 コードから、アサートを削除し、その後、ファイル、呼び出し元に方法を超える I/O アクセス許可の要求フローを使用する別の方法です。 これにより、セキュリティ チェックができます。 この場合、セキュリティ監査は必要ありません、ため、アクセス許可の要求は、呼び出し元や、アプリケーション ドメインにフローします。 アクセス許可の要求は、環境、およびソース コードのアクセス許可の付与をホストしている、セキュリティ ポリシーを通じて密接に制御されます。

## <a name="see-also"></a>関連項目
 [セキュリティの警告](../code-quality/security-warnings.md)