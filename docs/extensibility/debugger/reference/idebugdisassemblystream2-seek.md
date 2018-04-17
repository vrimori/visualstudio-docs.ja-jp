---
title: IDebugDisassemblyStream2::Seek |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55a8c2c205627130e8dd6dd28f288b2d3dee9d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[逆アセンブル] ストリームを指定した位置を基準とした命令数が特定の読み取りのポインターを移動します。  
  
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
 [in]値、 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)シーク プロセスを開始する相対位置を指定する列挙体です。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)を基準には、シーク操作コードのコンテキストを表すオブジェクト。 場合にのみ、このパラメーターは使用`dwSeekStart`  = `SEEK_START_CODECONTEXT`以外の場合、このパラメーターは無視され、null 値を指定できます。  
  
 `uCodeLocationId`  
 [in]相対シーク操作は、コードの場所の識別子です。 このパラメーターを使用`dwSeekStart`  = `SEEK_START_CODELOCID`以外の場合、このパラメーターは無視され、0 に設定することができます。 については、「解説」セクションを参照してください、 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)コード場所識別子の詳細についてはメソッドです。  
  
 `iInstructions`  
 [in]指定された位置を基準に移動する命令の数`dwSeekStart`です。 この値は、負の値を前後に移動することができます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`シーク位置が使用可能な命令の一覧より後ろにあった場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 リストの先頭より前に、の位置をシークであった場合は、読み取り位置が、一覧の最初の命令に設定されます。 参照は、リストの末尾後の位置には、読み取り位置は設定最後の命令一覧にされます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)