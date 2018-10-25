---
title: DISASSEMBLY_STREAM_SCOPE |Microsoft Docs
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
ms.openlocfilehash: 860d563abd5922ecf0461ed5f03ffa231ba9450f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831160"
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
 コードのコンテキストを逆アセンブルする生成クライアントは、1 回の呼び出しで取得するが通常よりも多くの出力を指定します。  
  
 DSS_FUNCTION  
 コードのコンテキストに含まれる関数を逆アセンブルすることを指定します。 によって返されるときに混合モードのストリームが、関数を表すことを指定、 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)メソッド。  
  
 DSS_MODULE  
 によって返されるときに、`IDebugDisassemblyStream2::GetScope`メソッドでは、混合モードのストリームがモジュールを表すことを指定します。  
  
 DSS_ALL  
 アドレス空間全体の逆アセンブリを指定します。  
  
## <a name="remarks"></a>Remarks  
 引数として渡される、 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)メソッドによって返されると、 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)メソッド。  
  
 これらの値は、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)