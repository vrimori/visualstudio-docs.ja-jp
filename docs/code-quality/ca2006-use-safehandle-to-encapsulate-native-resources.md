---
title: "Ca 2006: 使用 SafeHandle をネイティブ リソースをカプセル化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b83aec0a44e0762ed2d65f9bbbd39318b1b1b942
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: SafeHandle を使用して、ネイティブ リソースを要約します
|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|カテゴリ|Microsoft.Reliability|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 マネージ コードが<xref:System.IntPtr>ネイティブ リソースにアクセスします。  
  
## <a name="rule-description"></a>規則の説明  
 使用`IntPtr`マネージ コードで潜在的なセキュリティおよび信頼性の問題がある可能性があります。 すべての利用`IntPtr`をレビューする必要があるかどうかの使用、 <xref:System.Runtime.InteropServices.SafeHandle> 、または類似のテクノロジが、代わりに必要です。 問題が発生する場合、`IntPtr`メモリ、ファイル ハンドル、またはマネージ コードが所有すると見なされること、ソケットなどのいくつかのネイティブ リソースを表します。 マネージ コードに、リソースを所有している場合に関連付けられているネイティブ リソースも解放そのためにはエラーには、リソース リークが発生するために必要があります。  
  
 このようなシナリオでセキュリティあるいは信頼性の問題も存在するマルチ スレッド アクセスが許可された場合、`IntPtr`で表されるリソースを解放する方法と、`IntPtr`が指定されています。 これらの問題に関係のリサイクル、`IntPtr`値をリソースの解放中に、別のスレッドで同時に、リソースの使用が行われています。 これにより、競合状態の 1 つのスレッドが読み取りまたは間違ったリソースに関連付けられているデータを書き込む場所が発生することができます。 たとえば、次の型として、OS ハンドルに格納、`IntPtr`と、両方を呼び出すユーザー**閉じる**し、他のメソッドの同期の何らかと同時にそのハンドルを使用する、コードがハンドルのリサイクル問題があります。  
  
 このハンドルのリサイクル問題には、データが破損したり、多くの場合、セキュリティの脆弱性可能性があります。 `SafeHandle`その兄弟クラス<xref:System.Runtime.InteropServices.CriticalHandle>このようなスレッド処理の問題を回避するように、リソースへのネイティブ ハンドルをカプセル化するためのメカニズムを提供します。 また、使用することができます`SafeHandle`とその兄弟クラス`CriticalHandle`他のスレッド問題については、たとえば、ネイティブ メソッドの呼び出しを経由でのネイティブ ハンドルのコピーが含まれている管理対象オブジェクトの有効期間を慎重に制御します。 このような状況への呼び出しを削除することが多くの場合、`GC.KeepAlive`です。 使用する場合に発生するパフォーマンス オーバーヘッド中`SafeHandle`と度より低いレベル、 `CriticalHandle`、慎重に設計で頻繁に低下することができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 変換`IntPtr`使用量を`SafeHandle`ネイティブ リソースへのアクセスを安全に管理します。 参照してください、<xref:System.Runtime.InteropServices.SafeHandle>例については、リファレンス トピックです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この警告は抑制しないでください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IDisposable>