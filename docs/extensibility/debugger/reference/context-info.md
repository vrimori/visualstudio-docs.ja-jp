---
title: "CONTEXT_INFO |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 46168fefd491aeeae05c6406bd2b985fc5649bd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="contextinfo"></a>CONTEXT_INFO
この構造体は、メモリ コンテキストまたはコードのコンテキストについて説明します。  
  
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
 彼のフラグの組み合わせ[CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)のどのフィールドが埋められますを指定する列挙**です。**  
  
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
 特定のコンテキストが配置されているメモリ内の絶対アドレスです。  
  
## <a name="remarks"></a>コメント  
 この構造体への呼び出しから返される、 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)メソッドです。  
  
 サポートには、この構造体の一般的な使用、**メモリ**デバッグ ウィンドウです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)