---
title: "IDebugSyncOperation インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSyncOperation インターフェイス"
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation インターフェイス
入れ子の中に特定のブロックされたスレッドでスクリプト エンジンがその操作 \(式の評価など\) を抽出できるようになります実行する必要があります。  インターフェイスは、応答しなくなったような操作をキャンセルする機能を提供します。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugSyncOperation` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|この同期操作のターゲット アプリケーションのスレッドを返します。|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|同期的に処理し、を返します。|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|別のスレッドで実行中の操作をキャンセルします。|