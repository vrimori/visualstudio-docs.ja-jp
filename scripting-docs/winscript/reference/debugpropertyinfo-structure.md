---
title: "DebugPropertyInfo 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugPropertyInfo 構造体"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugPropertyInfo 構造体
名前、型、および値を持つ階層的な性質オブジェクトを表します。  ローカル変数のデバッグ プロパティを、パラメーター、ウォッチ変数、式、およびレジスタ記述するために使用されます。  
  
## 構文  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## メンバー  
 dwValidFields  
 フィールドが初期化される場所を指定する列挙型。  
  
 bstrName  
 コンテキスト内のプロパティ名。  
  
 bstrType  
 書式設定された文字列としてプロパティ型。  
  
 bstrValue  
 書式設定された文字列としてプロパティ値。  
  
 bstrFullName  
 プロパティの完全名。  
  
 dwAttrib  
 デバッグ プロパティのフラグを指定する列挙種別です。  
  
 pDebugProp  
 この `DebugPropertyInfo` の構造で情報で説明されている `IDebugProperty`。  
  
## 参照  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)