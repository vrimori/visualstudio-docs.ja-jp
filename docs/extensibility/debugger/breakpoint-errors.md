---
title: "ブレークポイント エラー | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ブレークポイント エラー"
  - "[デバッグ SDK] ブレークポイント エラーのデバッグ"
  - "エラー [SDK のデバッグ]"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ブレークポイント エラー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次のコードはブレークポイントにバインドしようとすると失敗について説明します。このプロセスは :  
  
## ブレークポイントのエラーのトラブルシューティング  
  
1.  デバッグ エンジンは \(DE\)デバッグ セッションのマネージャー \(SDM\) に [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) を送信します。  
  
2.  [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(SDM は IDebugErrorBreakpoint2 \*\* エラーのブレークポイントを取得するに `ppErrorBP`\) を呼び出します。  
  
3.  SDM はエラーが発生したブレークポイントの保留中のブレークポイントを取得するに [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) を呼び出します。  
  
4.  SDM はエラーのブレークポイントにバインドできなかった原因原因を取得するに [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) を呼び出します。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)