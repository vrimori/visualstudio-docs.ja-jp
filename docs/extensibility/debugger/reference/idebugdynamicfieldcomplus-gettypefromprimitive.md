---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive"
  - "GetTypeFromPrimitive"
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プリミティブ型を指定する型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetTypeFromPrimitive(  
   DWORD         dwCorElementType,  
   IDebugField** ppType  
);  
```  
  
```c#  
int GetTypeFromPrimitive(  
   uint            dwCorElementType,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwCorElementType`  
 [in]値、 [CorElementType 列挙型](CorElementType%20Enumeration.xml) プリミティブ型を表します。  
  
 `ppType`  
 [out]返します。、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 型を表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す `S_OK`。 そうしないと、エラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)