---
title: "FRAMEINFO |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FRAMEINFO
helpviewer_keywords: FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31f87c5261db32e19c9382d4d9cd95f4081cbe19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="frameinfo"></a>FRAMEINFO
スタック フレームを説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```csharp  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## <a name="members"></a>メンバー  
 m_dwValidFields  
 フラグの組み合わせ、 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)のどのフィールドが入力を指定する列挙です。  
  
 m_bstrFuncName  
 スタック フレームに関連付けられている関数の名前。  
  
 m_bstrReturnType  
 スタック フレームに関連付けられた戻り値の型。  
  
 m_bstrArgs  
 スタック フレームに関連付けられている関数の引数。  
  
 m_bstrLanguage  
 関数が実装されている言語です。  
  
 m_bstrModule  
 スタック フレームに関連付けられているモジュールの名前。  
  
 m_addrMin  
 最小の物理的なスタックのアドレス。  
  
 m_addrMAX  
 最大物理スタックのアドレス。  
  
 m_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)このスタック フレームを表すオブジェクト。  
  
 m_pFrame  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)このスタック フレームが含まれているモジュールを表すオブジェクト。  
  
 m_fHasDebugInfo  
 0 以外の値 (`TRUE`) 特定のフレームにデバッグ情報が存在する場合。  
  
 m_fHasDebugInfo  
 0 以外の値 (`TRUE`) 場合は、スタック フレームは無効になっているコードに関連付けられています。  
  
 m_fHasDebugInfo  
 0 以外の値 (`TRUE`) 場合は、セッション デバッグ マネージャー (SDM) によって、スタック フレームの注釈が付けられています。  
  
## <a name="remarks"></a>コメント  
 この構造体に渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)格納するメソッド。 この構造体が一覧に含まれているにも含まれている、 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)インターフェイス、さらへの呼び出しから返される、 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)