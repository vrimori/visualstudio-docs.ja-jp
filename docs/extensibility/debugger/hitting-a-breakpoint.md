---
title: "ブレークポイントにヒット | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] のデバッグ、ブレークポイントにヒット"
  - "ブレークポイントのヒット"
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# ブレークポイントにヒット
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次はデバッグ エンジンはブレークポイントにヒットしたら \(DE\) プロセスを説明します。実行時または実行します :  
  
## ブレークポイントのヒットのトラブルシューティング  
  
1.  DE sends **EVENT\_SYNC\_STOP** として [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) のインターフェイス。  
  
2.  デバッグ セッションのマネージャーは \(SDM\) ヒットしたブレークポイントを取得するに [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) を呼び出します。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)