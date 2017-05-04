---
title: "IJsDebugDataTarget::WriteMemory メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::WriteMemory メソッド
ターゲット プロセスのメモリを読み取ります。  
  
## 構文  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### パラメーター  
 `address`  
 \[入力\] ターゲット プロセスのメモリの書き込み元のベース アドレス。  
  
 `pMemory`  
 \[入力\] 指定したプロセスのアドレス空間に書き込むデータ。  
  
 `size`  
 \[入力\] プロセスに書き込むバイト数。  
  
## 戻り値  
  
## 解説  
 データ転送が行われる前に、ベース アドレスのすべてのデータと指定したサイズのメモリに書き込みアクセスが可能であることがシステムによって確認され、可能でない場合、この関数によって E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS エラーが発生します。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)