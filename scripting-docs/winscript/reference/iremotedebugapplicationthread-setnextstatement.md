---
title: "IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::SetNextStatement"
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::SetNextStatement
特定のコード コンテキストに、特定のフレームのコンテキストで実行を継続できるだけ近い累乗。  
  
## 構文  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### パラメーター  
 `pStackFrame`  
 \[出力\]スタック フレーム オブジェクト。  現在のスタック フレームを使用する必要がある場合、この引数は null である可能性があります。  
  
 `pCodeContext`  
 \[入力\]コード コンテキスト。  現在のコンテキスト コードを使用する必要がある場合、この引数は null である可能性があります。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは `pStackFrame`で指定されたフレームのコンテキストで `pCodeContext`で指定されているコード コンテキストにできるだけ近い続行するために実行を強制します。  これらの引数の `NULL`の可能性が現在のフレームまたはコンテキストを表します。  
  
## 参照  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)