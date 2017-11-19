---
title: "IDebugDisassemblyStream2::Seek |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Seek
helpviewer_keywords: IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61ef1e649a80fcda5ec3ce4be6c74b154c17f9a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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