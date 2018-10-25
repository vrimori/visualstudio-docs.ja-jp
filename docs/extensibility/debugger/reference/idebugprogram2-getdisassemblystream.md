---
title: IDebugProgram2::GetDisassemblyStream |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8d2220d928128b02ea02d26f8273714a89171ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896459"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
このプログラムまたはこのプログラムの一部の逆アセンブリのストリームを取得します。  
  
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
 [in]値を指定します、 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)逆アセンブリのストリームのスコープを定義する列挙です。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)逆アセンブリのストリームを開始する位置を表すオブジェクト。  
  
 `ppDisassemblyStream`  
 [out]返します、 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)逆アセンブリのストリームを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 返します`E_DISASM_NOTSUPPORTED`逆アセンブリがこの特定のアーキテクチャのサポートされていない場合。  
  
## <a name="remarks"></a>Remarks  
 場合、`dwScopes`パラメーターには、`DSS_HUGE`のフラグ、 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)列挙型を設定し、ファイル全体の逆アセンブリ命令の数が多いを返す、逆アセンブルが必要ですまたはモジュール。 場合、`DSS_HUGE`フラグが設定されていない、逆アセンブルされることに、小さな領域に限定する 1 つの関数の通常します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)