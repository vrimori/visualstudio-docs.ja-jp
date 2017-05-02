---
title: "ISimpleConnectionPoint::GetEventCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.GetEventCount
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::GetEventCount"
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::GetEventCount
このインターフェイスで公開されるイベント数を返します。  
  
## 構文  
  
```  
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### パラメーター  
 `pulCount`  
 \[出力\]このインターフェイスの計算に公開するイベントの数。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このインターフェイスで公開されるイベント数を返します。  
  
## 参照  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)