---
title: "信頼性の警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "警告、信頼性"
  - "信頼性に関する警告"
  - "マネージ コード分析に関する警告、信頼性に関する警告"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 信頼性の警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

信頼性の警告は、メモリやスレッドの適切な使用など、ライブラリとアプリケーションの信頼性をサポートします。  
  
## このセクションの内容  
  
|規則|説明|  
|--------|--------|  
|[CA2000: スコープが失われる前にオブジェクトを破棄します](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|例外的なイベントが発生するとオブジェクトのファイナライザーを実行できないため、オブジェクトに対するすべての参照がスコープ外になる前に、オブジェクトを明示的に破棄する必要があります。|  
|[CA2001: 問題が発生する可能性のあるメソッドは呼び出しません](../Topic/CA2001:%20Avoid%20calling%20problematic%20methods.md)|メンバーが危険性または問題のあるメソッドを呼び出します。|  
|[CA2002: ID が不十分なオブジェクトをロックしないでください](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|アプリケーション ドメインの境界を越えてオブジェクトに直接アクセスできる場合、そのオブジェクトの ID は不十分と表現されます。  スレッドで ID が不十分なオブジェクトをロックしようとすると、ブロックされることがあります。たとえば、異なるアプリケーション ドメインの別スレッドで、既に同じオブジェクトがロックされている場合です。|  
|[CA2003: ファイバーをスレッドとして扱いません](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|マネージ スレッドが Win32 スレッドとして扱われています。|  
|[CA2004: GC.KeepAlive への呼び出しを削除します](../Topic/CA2004:%20Remove%20calls%20to%20GC.KeepAlive.md)|SafeHandle の使用に変更する場合、すべての GC.KeepAlive \(object\) の呼び出しを削除します。  この場合、クラスに GC.KeepAlive の呼び出しを含めることはできません。クラスはファイナライザーを持っていない代わりに、SafeHandle を使用して OS ハンドルを終了していることが前提となっています。|  
|[CA2006: SafeHandle を使用して、ネイティブ リソースを要約します](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|マネージ コードで IntPtr を使用すると、セキュリティ上の問題および信頼性の問題が発生する可能性があります。  すべての IntPtr の使用状況をチェックして、SafeHandle または類似のテクノロジに置き換える必要があるかどうかを判断してください。|