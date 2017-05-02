---
title: "IJsDebugDataTarget::GetTlsValue メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetTlsValue メソッド
For the thread being debugged, retrieves the value in the thread local storage \(TLS\) slot for the specified TLS index.  
  
## 構文  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### パラメーター  
 `threadId`  
 \[入力\] 読み取り元となるターゲット プロセスで実行中のスレッド。  
  
 `tlsIndex`  
 \[入力\] ターゲット プロセスが TlsAlloc 関数を呼び出したときに割り当てられた TLS インデックス。  
  
 `pValue`  
 \[出力\] スレッドの TLS スロットに格納されたポインター サイズの値。  対象のスレッドが 32 ビットの場合、この値の上位 32 ビットがゼロになります。  
  
## 戻り値  
  
## 解説  
 プロセスの各スレッドには TLS インデックスごとに専用のスロットがあります。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)