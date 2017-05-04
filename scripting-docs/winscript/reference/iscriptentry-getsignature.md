---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
`IScriptEntry` の関数オブジェクトの型情報を返します。  
  
## 構文  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### パラメーター  
 `ppti`  
 \[出力\]この関数の `IScriptEntry` オブジェクトに関連付けられている情報を入力します。  
  
 `piMethod`  
 \[入力\] `ITypeInfo` のオブジェクトのメソッドのインデックス。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) か [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)を使用して設定に情報を入力します。  型情報は、内部関数の表示に基づいてエントリに生成されることがあります。  
  
## 参照  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)