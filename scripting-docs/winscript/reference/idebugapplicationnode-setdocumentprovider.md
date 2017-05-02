---
title: "IDebugApplicationNode::SetDocumentProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.SetDocumentProvider
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::SetDocumentProvider"
ms.assetid: 7cb587ca-d84e-4b5e-9b94-e973cca55a03
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::SetDocumentProvider
このアプリケーション ノードのドキュメントのプロバイダーを設定します。  
  
## 構文  
  
```  
HRESULT SetDocumentProvider(  
   IDebugDocumentProvider*  pddp  
);  
```  
  
#### パラメーター  
 `pddp`  
 \[出力\]このアプリケーション ノードのドキュメントのプロバイダー。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このアプリケーション ノードのドキュメントのプロバイダーを設定します。  
  
## 参照  
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)