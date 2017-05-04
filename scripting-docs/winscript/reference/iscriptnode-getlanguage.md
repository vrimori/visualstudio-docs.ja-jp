---
title: "IScriptNode::GetLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetLanguage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetLanguage"
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IScriptNode::GetLanguage
現在のスクリプトのノードで使用されるスクリプト言語を返します。  
  
## 構文  
  
```  
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### パラメーター  
 `pbstr`  
 \[スクリプト\]ノードが Visual Basic Scripting Edition \(VBScript\) を使用してスクリプトのノードが JScript を使用する場合は、「スクリプト」VB 「JScript」を返します。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)