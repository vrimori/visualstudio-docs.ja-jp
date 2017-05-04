---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
現在のスレッドをブロックするに説明し、デバッガーのブレークポイント IDE に通知を送信します。  
  
## 構文  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### パラメーター  
 `br`  
 \[入力\]中断の理由。  
  
 `pbra`  
 \[入力\]デバッガーでアプリケーションを再開したときに実行するアクション。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 言語エンジンは、ブレークポイントにヒットしたスレッドのコンテキストでこのメソッドを呼び出します。  このメソッドは、現在のスレッドをブロックせず、デバッガーのブレークポイント IDE に通知を送信します。  デバッガーでアプリケーションを再開すると、`pbra` のパラメーターは、アクションを指定します。  
  
> [!NOTE]
>  言語エンジンは、スレッドがタスクをのようなするために列挙するか、スタック フレームやブレークポイントの間に評価される式を呼び出すことがあります。  
  
 このメソッドは `IApplicationDebugger::onHandleBreakPoint` を呼び出します。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)