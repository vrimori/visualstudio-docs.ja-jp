---
title: "IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ResumeFromBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ResumeFromBreakPoint"
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ResumeFromBreakPoint
ブレークポイントに存在するアプリケーションを続行します。  
  
## 構文  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### パラメーター  
 `prptFocus`  
 \[入力\]ステップのモードの場合、手順のモードによって影響を受けるスレッド。  
  
 `bra`  
 \[入力\]アプリケーションを再開したときに実行するアクション。  
  
 `era`  
 \[出力\]アプリケーションがエラーで停止した場合に実行するアクション。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、ブレークポイントに存在するアプリケーションを続行します。  
  
## 参照  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列挙型](../../winscript/reference/errorresumeaction-enumeration.md)