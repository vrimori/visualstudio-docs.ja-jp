---
title: CONTEXT_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a88a1a3c2d07387399a1701b6645d300bce8993d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927247"
---
# <a name="contextinfo"></a>CONTEXT_INFO
この構造体には、メモリのコンテキストまたはコードのコンテキストについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwFields  
 彼からフラグの組み合わせ[CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)フィールドが記入を指定する列挙体<strong>します。</strong>  
  
 bstrModuleUrl  
 コンテキストが配置されているモジュールの名前。  
  
 bstrFunction  
 コンテキストが配置されている関数の名前。  
  
 posFunctionOffset  
 A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)コードのコンテキストに関連付けられている関数の行と列のオフセットを識別する構造体。  
  
 bstrAddress  
 指定されたコンテキストが配置されているコード内のアドレス。  
  
 bstrAddressOffset  
 指定されたコンテキストが配置されているコード内のアドレスのオフセット。  
  
 bstrAddressAbsolute  
 指定されたコンテキストが配置されているメモリ内で絶対アドレスです。  
  
## <a name="remarks"></a>Remarks  
 この構造体がへの呼び出しから返される、 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)メソッド。  
  
 この構造体の一般的な用途は、のサポートには、**メモリ**デバッグ ウィンドウ。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)