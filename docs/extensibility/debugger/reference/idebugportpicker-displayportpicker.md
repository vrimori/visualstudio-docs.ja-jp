---
title: "IDebugPortPicker::DisplayPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayPortPicker"
  - "IDebugPortPicker::DisplayPortPicker"
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポートをユーザーが選択できるように指定するダイアログ ボックスが表示されます。  
  
## 構文  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```c#  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### パラメーター  
 `hwndParentDialog`  
 \[入力\] 親ダイアログ ボックスのハンドル。  
  
 `pbstrPortId`  
 \[入力\] ポートの識別子の文字列。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  ユーザーが \[ENT1ENT\] をクリックしを `S_FALSE` の戻り値 \(または `NULL` への `BSTR` に設定 `S_OK` の戻り値\) を表示します。  
  
## 参照  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)