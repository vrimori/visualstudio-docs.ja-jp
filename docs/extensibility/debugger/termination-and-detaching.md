---
title: "終了とデタッチ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プログラムの終了イベント"
  - "デバッグ エンジンは、プログラムからのデタッチ"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 終了とデタッチ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次に通常の終了を示します。  
  
## 説明  
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) または [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) の後にインターフェイスは完了時にデバッグ アプリケーションにブレークポイント例外ランタイム エラーまたは無限ループがなければデバッグ動作するプログラムです。  これは正常に終了します。  
  
 実装の標準の終了に [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) を送信する必要があります。  これは [IDebugProgramDestroyEvent2:: GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md) メソッドの実装が必要です。  
  
## 参照  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)