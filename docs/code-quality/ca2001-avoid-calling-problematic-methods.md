---
title: "Ca 2001: 問題のあるメソッドは呼び出しません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ca28bc1fd6a76262b47800dcca466e8843d3271
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: 問題が発生する可能性のあるメソッドは呼び出しません
|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|CheckId|CA2001|  
|カテゴリ|Microsoft.Reliability|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 メンバーが危険性または問題のあるメソッドを呼び出します。  
  
## <a name="rule-description"></a>規則の説明  
 不要なと危険性のあるメソッド呼び出しを行うしないでください。  
  
 この規則の違反は、メンバーが次の方法の 1 つを呼び出すときに発生します。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC を呼び出しています。収集は、アプリケーションのパフォーマンスに影響する可能性が大幅に、必要はほとんどありません。 詳細については、次を参照してください。、 [Rico Mariani パフォーマンス Tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) MSDN のブログ エントリです。|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend および Thread.Resume は、予測できない動作のため推奨されません。  他のクラスを使用して、<xref:System.Threading>名前空間など<xref:System.Threading.Monitor>、 <xref:System.Threading.Mutex>、 <xref:System.Threading.Mutex>、および<xref:System.Threading.Semaphore>スレッドを同期させるか、リソースを保護します。|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle メソッドは、無効なハンドルを返すことができるため、セキュリティ上のリスクを招きます。 参照してください、<xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>と<xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>DangerousGetHandle メソッドを安全に使用する方法の詳細についてのメソッドです。|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|これらのメソッドは、予期しない場所からアセンブリを読み込むことができます。 たとえば、Suzanne Cook の .NET CLR ノート ブログの投稿を参照してください[LoadFile vs です。LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450)と[バインディング コンテキストを選択する](http://go.microsoft.com/fwlink/?LinkId=164451)アセンブリを読み込む方法については、MSDN Web サイトにします。|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|ユーザー コードでは、マネージ プロセスで実行が開始時刻は遅すぎます CoSetProxyBlanket を確実に呼び出すです。 共通言語ランタイム (CLR) は成功からユーザー P/invoke を妨げる可能性のある初期化操作を実行します。<br /><br /> マネージ アプリケーションの CoSetProxyBlanket を呼び出すが、ネイティブ コード (C++) の実行可能ファイルを使用してプロセスを開始し、ネイティブ コードで CoSetProxyBlanket を呼び出すプロセスで、マネージ コード アプリケーションを起動をお勧めします。 (するランタイムのバージョン番号を指定してください)。|  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するのには、削除するか、危険性または問題のあるメソッドの呼び出しを置き換えます。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 問題のあるメソッドに代わる方法が使用できない場合にのみ、この規則からのメッセージを抑制する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [信頼性の警告](../code-quality/reliability-warnings.md)