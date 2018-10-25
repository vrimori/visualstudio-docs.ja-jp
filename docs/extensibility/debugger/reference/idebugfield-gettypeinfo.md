---
title: IDebugField::GetTypeInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dfc82e7450c88420cfca50c74a3ac9451a78b095
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925995"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
このメソッドは、シンボルまたは型の型に依存しない情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pTypeInfo`  
 [out]指定された型情報を返します[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 型に依存しない情報が含まれます、たとえば、AppDomain、モジュール、および記号を格納するクラス。  
  
## <a name="see-also"></a>関連項目  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)