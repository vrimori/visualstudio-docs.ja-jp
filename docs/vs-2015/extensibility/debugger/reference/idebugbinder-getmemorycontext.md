---
title: IDebugBinder::GetMemoryContext |Microsoft Docs
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
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e0c9d7dbcd20407d81ccfc7ed0d8f63cdeec974
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548038"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugBinder::GetMemoryContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder-getmemorycontext)します。  
  
このメソッドでは、メモリのコンテキストにオブジェクトの場所またはメモリ アドレスのいずれかに変換します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)検索するオブジェクトを記述します。 場合`NULL`を使用して`dwConstant`代わりにします。  
  
 `dwConstant`  
 [in]0x5000 などの定数のメモリ アドレス。  
  
 `ppMemCxt`  
 [out]返します、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)オブジェクトのアドレス、またはメモリ内のアドレスを表すインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

