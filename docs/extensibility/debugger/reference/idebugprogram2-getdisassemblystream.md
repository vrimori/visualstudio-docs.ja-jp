---
title: "IDebugProgram2::GetDisassemblyStream |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 50655e8d565fe08c4ea918d69f5eeb8780d43c55
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
このプログラムまたはこのプログラムの一部の逆アセンブリ ストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwScope`  
 [in]値を指定して、 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)逆アセンブル ストリームのスコープを定義する列挙値。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)を逆アセンブル ストリームを開始する場所の位置を表すオブジェクト。  
  
 `ppDisassemblyStream`  
 [out]返します、 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)を逆アセンブル ストリームを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_DISASM_NOTSUPPORTED`逆アセンブリがこの特定のアーキテクチャのサポートされていない場合。  
  
## <a name="remarks"></a>コメント  
 場合、`dwScopes`パラメーターには、`DSS_HUGE`のフラグ、 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)列挙セットし、逆アセンブルをファイル全体の逆アセンブリ命令の数が多いを返すと予想されます。またはモジュール。 場合、`DSS_HUGE`フラグが設定されていない、し、逆アセンブルを小さな領域に限定すると予想される 1 つの関数の通常のです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
