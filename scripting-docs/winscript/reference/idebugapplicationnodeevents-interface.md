---
title: "IDebugApplicationNodeEvents インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents インターフェイス"
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents インターフェイス
`IDebugApplicationNode` のインターフェイスにイベント インターフェイスを提供します。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugApplicationNodeEvents` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|子ノードが、デバッグ アプリケーションのオブジェクト ノードに追加されたときにイベントを処理します。|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|子ノードがデバッグのアプリケーション ノード オブジェクトから削除されたときにイベントを処理します。|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|デバッグ イベントのアプリケーション ノード オブジェクトが親ノードからデタッチされたことを示します処理します。|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|イベントを親ノードにデバッグ アプリケーションのオブジェクト ノードがアタッチされたことを示します処理します。|  
  
## 参照  
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)