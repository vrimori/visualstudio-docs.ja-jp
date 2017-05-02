---
title: "IDebugApplicationNodeEvents::onRemoveChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onRemoveChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onRemoveChild"
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onRemoveChild
子ノードがデバッグのアプリケーション ノード オブジェクトから削除されたときにイベントを処理します。  
  
## 構文  
  
```  
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### パラメーター  
 `prddpChild`  
 \[入力\]削除された子アプリケーションのノード。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、子ノードがデバッグのアプリケーション ノード オブジェクトから削除されたときにイベントを処理します。  
  
 `IDebugApplicationNode` のインターフェイスの実装では、このイベントを発生させます。  
  
## 参照  
 [IDebugApplicationNodeEvents インターフェイス](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)