---
title: "IScriptNode::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetParent"
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetParent
オブジェクトの親である `IScriptNode` のオブジェクトを返します。  
  
## 構文  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### パラメーター  
 `ppsnParent`  
 \[入力\]親のインスタンスの `IScriptNode` のインターフェイスへのポインターを受け取る変数のアドレス。  
  
 クラスの実装 `IScriptEntry` か `IScriptScriptlet`が、`IScriptNode` のオブジェクトが返されます。  
  
 クラスが `IScriptNode` \(Web ページを表します\) 実行すると、NULL が返されます。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)