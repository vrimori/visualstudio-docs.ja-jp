---
title: IDebugDisassemblyStream2::Seek |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a2c3cf1a1a5ee17a3ecdb6ed6b097b3ff4dde18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976707"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[逆アセンブル] ストリームの指定した位置の基準とした命令数が特定の読み取りポインターを移動します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwSeekStart`  
 [in]値、 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)シーク プロセスを開始する相対位置を指定する列挙体。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)シーク操作が関連してコードのコンテキストを表すオブジェクト。 場合にのみ、このパラメーターが使用される`dwSeekStart`  =  `SEEK_START_CODECONTEXT`。 そうしないと、このパラメーターは無視され、null 値を指定できます。  
  
 `uCodeLocationId`  
 [in]シーク操作が関連してコードの場所の識別子です。 このパラメーターを使用`dwSeekStart`  =  `SEEK_START_CODELOCID`。 そうしないと、このパラメーターは無視され、0 に設定することができます。 「解説」を参照してください、 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)メソッドについては、コードの場所の識別子。  
  
 `iInstructions`  
 [in]指定された位置を基準に移動する命令数`dwSeekStart`します。 この値は、後方に移動する負の値であることができます。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`シーク位置が使用可能な命令の一覧より後ろにあった場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 リストの先頭の前に、シークであった場合は、読み取り位置が、一覧の最初の命令に設定されます。 参照してくださいがあった場合の位置に、リストの末尾の後に、読み取り位置が設定最後の命令の一覧で。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)