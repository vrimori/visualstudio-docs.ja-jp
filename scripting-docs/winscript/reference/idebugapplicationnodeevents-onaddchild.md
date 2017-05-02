---
title: "IDebugApplicationNodeEvents::onAddChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onAddChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onAddChild"
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onAddChild
子ノードが、デバッグ アプリケーションのオブジェクト ノードに追加されたときにイベントを処理します。  
  
## 構文  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### パラメーター  
 `prddpChild`  
 \[入力\]追加された機能のデバッグ アプリケーションのノード。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、子ノードが、デバッグ アプリケーションのオブジェクト ノードに追加されたときにイベントを処理します。  
  
 `IDebugApplicationNode` のインターフェイスの実装では、このイベントを発生させます  
  
## 参照  
 [IDebugApplicationNodeEvents インターフェイス](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)