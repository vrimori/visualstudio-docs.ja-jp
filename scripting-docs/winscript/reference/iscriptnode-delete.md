---
title: "IScriptNode::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Delete"
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::Delete
このオブジェクト ツリーを削除します。  
  
## 構文  
  
```  
HRESULT Delete();  
```  
  
#### パラメーター  
 メソッドはパラメーターを受け取りません。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `Delete` のメソッドが呼び出された後、[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) のメソッドは、スクリプトのノードがアクティブではないことを示す必要があります。  
  
## 参照  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)