---
title: "IDebugModule2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "GetInfo メソッド"
  - "IDebugModule2::GetInfo メソッド"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このモジュールに関する情報を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### パラメーター  
 `dwFields`  
 \[入力\] `pInfo` のフィールドを表示するかを指定します [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) の列挙体のフラグの組み合わせ。  
  
 `pInfo`  
 \[入力出力\] モジュールの説明が格納されます [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) の構造体。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) の構造体には\[出力\] ウィンドウに表示 ENT0ENT のモジュールの名前が含まれています。  
  
## 参照  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)