---
title: "IDebugApplicationNode::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.Detach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::Detach"
ms.assetid: 36bb3e54-a4df-48d5-a6de-3b8d4c0e98a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::Detach
プロジェクト ツリーからこのアプリケーション ノードを削除します。  
  
## 構文  
  
```  
HRESULT Detach();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、プロジェクト ツリーからこのアプリケーション ノードを削除します。  
  
## 参照  
 [IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)   
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)