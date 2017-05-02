---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
ノードの指定したインデックス位置にある子を返します。  
  
## 構文  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### パラメーター  
 `isn`  
 \[入力\]親の子のインデックス。  
  
 `ppsn`  
 \[入力\]子のインスタンスの `IScriptNode` のインターフェイスへのポインターを受け取る変数のアドレス。  
  
 Web ページを表す `IScriptNode` のオブジェクトの場合、このパラメーターはスクリプトのブロックを含むオブジェクト。  
  
 スクリプトのブロックを指定する `IScriptEntry` のオブジェクトに対する、この関数の戻り値パラメーターを指定するオブジェクト。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `IScriptScriptlet` のオブジェクトに対して関数オブジェクトを指定する `IScriptEntry` のオブジェクトの子のエントリがないため、このメソッドは失敗します。  
  
## 参照  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)