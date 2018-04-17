---
title: DISASSEMBLY_STREAM_SCOPE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0c72d0f14da9840c0a77d5ae88cb0acb5b54cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
[逆アセンブル] ストリームのスコープを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>メンバー  
 DSS_HUGE  
 コードのコンテキストを分解すると、クライアントは 1 回の呼び出しで取得する必要が通常以上の出力が生成することを指定します。  
  
 DSS_FUNCTION  
 コードのコンテキストに含まれる関数を逆アセンブルすることを指定します。 によって返されるときに逆アセンブル ストリームが、関数を表すことを指定します、 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)メソッドです。  
  
 DSS_MODULE  
 によって返されるときに、`IDebugDisassemblyStream2::GetScope`メソッドは、逆アセンブル ストリームがモジュールを表すことを指定します。  
  
 DSS_ALL  
 アドレス空間全体の逆アセンブリを指定します。  
  
## <a name="remarks"></a>コメント  
 引数として渡される、 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)メソッドによって返されると、 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)メソッドです。  
  
 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)