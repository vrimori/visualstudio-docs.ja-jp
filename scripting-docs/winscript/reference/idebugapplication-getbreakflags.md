---
title: "IDebugApplication::GetBreakFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.GetBreakFlags
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::GetBreakFlags"
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::GetBreakFlags
アプリケーションの現在の中断のフラグを返します。  
  
## 構文  
  
```  
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### パラメーター  
 `pabf`  
 \[入力\]現在の中断がアプリケーションにフラグを設定します。  
  
 `pprdatSteppingThread`  
 \[出力\]現在実行中のスレッド。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、アプリケーションの現在の中断のフラグを返します。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [APPBREAKFLAGS 列挙型](../../winscript/reference/appbreakflags-enumeration.md)