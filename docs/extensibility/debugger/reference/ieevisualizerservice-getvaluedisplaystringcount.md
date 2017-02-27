---
title: "IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IEEVisualizerService::GetValueDisplayStringCount"
  - "GetValueDisplayStringCount"
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

値の文字列数を指定したプロパティに表示したりわかります。を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```c#  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### パラメーター  
 `displayKind`  
 \[入力\] [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) の列挙体の値。  
  
 `propertyOrField`  
 \[入力\] プロパティまたはフィールドを表す [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイス。  
  
 `pcelt`  
 \[入力\] 表示する値の文字列数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)