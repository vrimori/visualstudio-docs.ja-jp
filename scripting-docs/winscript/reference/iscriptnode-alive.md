---
title: "IScriptNode::Alive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Alive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Alive"
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptNode::Alive
オブジェクトがまだアクティブかどうかを示します。  
  
## 構文  
  
```  
HRESULT Alive();  
```  
  
#### パラメーター  
 メソッドはパラメーターを受け取りません。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|スクリプトのノードは依然としてアクティブです。|  
  
## 解説  
 オブジェクトがアクティブでない場合は、コンポーネント オブジェクト モデルは \(COM\) 呼び出しのマーシャリングのプロキシからこのメソッドにエラーを返します。  
  
## 参照  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)