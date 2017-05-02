---
title: "IRemoteDebugApplication::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CauseBreak
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CauseBreak"
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplication::CauseBreak
デバッガーにできるだけ早くアプリケーションを中断します。  
  
## 構文  
  
```  
HRESULT CauseBreak();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドを呼び出すと、直ちに中断アプリケーションは発生しません。  アプリケーションの現在のスクリプト コードを実行する、長時間は、アプリケーションが実際に中断する前にタイムアウトする場合があります。  
  
## 参照  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)