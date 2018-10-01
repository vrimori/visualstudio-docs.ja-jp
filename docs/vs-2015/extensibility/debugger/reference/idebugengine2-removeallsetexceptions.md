---
title: IDebugEngine2::RemoveAllSetExceptions |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 09951fb3f19866b5efd3dc1511ef465907efb398
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534398"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugEngine2::RemoveAllSetExceptions](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine2-removeallsetexceptions)します。  
  
例外は、IDE が特定のランタイム アーキテクチャまたは言語の設定の一覧を削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidType`  
 [in]言語の GUID または実行時のアーキテクチャに固有のデバッグ エンジンの GUID。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドによって削除された例外は、以前の呼び出しによって設定された、 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)メソッド。  
  
 特定の例外を削除するには、呼び出し、 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)

