---
title: DISASSEMBLY_STREAM_SCOPE |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fcc74d44e9a460156ac3ab8b14bf7dc407aea35
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257479"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

[逆アセンブル] ストリームのスコープを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)

