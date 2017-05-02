---
title: "IDebugApplicationNode::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.EnumChildren
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::EnumChildren"
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::EnumChildren
このアプリケーション ノードの子ノードを列挙します。  
  
## 構文  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### パラメーター  
 `pperddp`  
 \[出力\]このノードの子ノードの列挙体。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このアプリケーション ノードの子ノードを列挙します。  
  
## 参照  
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)