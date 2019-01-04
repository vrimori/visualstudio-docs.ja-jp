---
title: IDebugProcess2::GetInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13746b95ad37ad5d2c973ac9fe765975891288ec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860180"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
プロセスの説明を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Fields`  
 [in]値の組み合わせ、 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)のどのフィールドを指定する列挙体、`pProcessInfo`パラメーター入力します。  
  
 `pProcessInfo`  
 [out]A [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造体のプロセスの説明が入力されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)