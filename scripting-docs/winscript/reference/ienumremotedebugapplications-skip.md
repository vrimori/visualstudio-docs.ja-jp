---
title: "IEnumRemoteDebugApplications::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplications.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications::Skip"
ms.assetid: 9f6578d9-8de5-419c-b1b5-7cb07b6367fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications::Skip
列挙体シーケンス内の指定した数のセグメントをスキップします。  
  
## 構文  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### パラメーター  
 `celt`  
 \[スキップ\]列挙体シーケンス内の線分の数。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、列挙体シーケンスのセグメントの指定した数の要素をスキップします。  
  
## 参照  
 [IEnumRemoteDebugApplications インターフェイス](../../winscript/reference/ienumremotedebugapplications-interface.md)