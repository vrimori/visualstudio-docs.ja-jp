---
title: "CA2006: SafeHandle を使用して、ネイティブ リソースを要約します | Microsoft Docs"
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
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2006: SafeHandle を使用して、ネイティブ リソースを要約します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|分類|Microsoft.Reliability|  
|互換性に影響する変更点|なし|  
  
## 原因  
 マネージ コードが <xref:System.IntPtr> を使用してネイティブ リソースにアクセスしています。  
  
## 規則の説明  
 マネージ コードで `IntPtr` を使用すると、セキュリティ上の問題および信頼性の問題が発生する可能性があります。  すべての `IntPtr` の使用状況をチェックして、<xref:System.Runtime.InteropServices.SafeHandle> または類似のテクノロジに置き換える必要があるかを判断してください。  `IntPtr` が、マネージ コードの所有と見なされるメモリ、ファイル ハンドル、ソケットなどのネイティブ リソースを表す場合に問題が発生します。  マネージ コードがリソースを所有している場合は、関連付けられているネイティブ リソースを解放する必要もあります。解放に失敗するとリソース リークが発生します。  
  
 このシナリオでは、マルチスレッド アクセスが `IntPtr` に許可されている場合、または `IntPtr` によって表されているリソースを解放する方法が提供されている場合、セキュリティ上の問題または信頼性の問題も発生します。  これらの問題は、リソース解放時にそのリソースが別のスレッドで同時に使用されている場合に生じる `IntPtr` 値のリサイクルが関連しています。  このリサイクルから競合状態が発生し、片方のスレッドが、誤ったリソースに関連付けられたデータを読み書きする可能性があります。  たとえば、OS ハンドルを `IntPtr` として型に格納し、ユーザーがそのハンドルを使用する **Close** と他の任意のメソッドを同期させずに同時に両方とも呼び出す場合に、コードでハンドルのリサイクル問題が発生します。  
  
 このハンドルのリサイクル問題は、データの破損を引き起こし、セキュリティの脆弱性の原因となることがしばしばあります。  `SafeHandle` とその兄弟クラス <xref:System.Runtime.InteropServices.CriticalHandle> によって、リソースに対するネイティブ ハンドルをカプセル化する機構が提供されるため、このようなスレッド処理の問題を回避できます。  また、`SafeHandle` および兄弟クラス `CriticalHandle` は、他のスレッド問題にも使用できます。たとえば、ネイティブ メソッドの呼び出しに対するネイティブ ハンドルのコピーを格納するマネージ オブジェクトの有効期間を綿密に制御できます。  この場合、通常は `GC.KeepAlive` の呼び出しを削除します。  `SafeHandle` や `CriticalHandle` \(使用頻度は少ない\) を使用するときに生じるパフォーマンス オーバーヘッドは、注意深い設計によって低減できます。  
  
## 違反の修正方法  
 `IntPtr` の使用を `SafeHandle` に変更して、ネイティブ リソースへのアクセスを安全に管理します。  例については、<xref:System.Runtime.InteropServices.SafeHandle> のリファレンス トピックを参照してください。  
  
## 警告を抑制する状況  
 この警告は抑制しないでください。  
  
## 参照  
 <xref:System.IDisposable>