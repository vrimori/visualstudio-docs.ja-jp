---
title: IDebugBinder3::GetExceptionObjectAndType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 713d0ba674fc7ab763c04a36353688e790df3924
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887699"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
このメソッドは、存在する場合に、オブジェクトに関連付けられている例外を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppException`  
 [out]例外を表すオブジェクトを返します。  
  
 `ppField`  
 [out]例外を引き起こした可能性のある特定のフィールドを表すオブジェクトを返します（これはnull値かもしれません）。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  例外があるかどうかを確認するには、によって返される値を確認`ppException`: かどうかは null 値をこのオブジェクトに関連付けられた例外はありません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)