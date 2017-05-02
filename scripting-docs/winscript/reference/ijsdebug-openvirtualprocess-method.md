---
title: "IJsDebug::OpenVirtualProcess メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebug::OpenVirtualProcess メソッド
Factory method used to create a new virtual process object.  
  
## 構文  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### パラメーター  
 `processId`  
 \[入力\] デバッガーをアタッチするプロセス ID。  
  
 `runtimeJsBaseAddress`  
 \[入力\] JavaScript ランタイムがターゲット プロセスに読み込まれるベース アドレス。  
  
 `pDataTarget`  
 \[入力\] プロセスの状態を照会するために使用するデバッガーに付属のインターフェイス。  
  
 `ppProcess`  
 \[出力\] 新しいデバッグ プロセス オブジェクト。  
  
## 戻り値  
  
## 解説  
 Jscript9diag と Jscript9 が一致しない場合は E\_JsDEBUG\_MISMATCHED\_RUNTIME を返します。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebug インターフェイス](../../winscript/reference/ijsdebug-interface.md)