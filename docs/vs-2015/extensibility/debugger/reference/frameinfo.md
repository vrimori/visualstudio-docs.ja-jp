---
title: FRAMEINFO |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 00590f4ce9822eee9253196aba15019eb86de1b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536363"
---
# <a name="frameinfo"></a>FRAMEINFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[FRAMEINFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/frameinfo)します。  
  
スタック フレームをについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 フラグの組み合わせ、 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)どのフィールドに入力を指定する列挙体。  
  
 m_bstrFuncName  
 スタック フレームに関連付けられている関数の名前。  
  
 m_bstrReturnType  
 スタック フレームに関連付けられている戻り値の型。  
  
 m_bstrArgs  
 スタック フレームに関連付けられている関数の引数。  
  
 m_bstrLanguage  
 関数が実装される言語です。  
  
 m_bstrModule  
 スタック フレームに関連付けられているモジュール名。  
  
 m_addrMin  
 最小物理スタック アドレス。  
  
 m_addrMAX  
 最大物理スタック アドレス。  
  
 m_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)このスタック フレームを表すオブジェクト。  
  
 m_pFrame  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)をこのスタック フレームを含むモジュールを表すオブジェクト。  
  
 m_fHasDebugInfo  
 0 以外の値 (`TRUE`) 特定のフレームにデバッグ情報が存在する場合。  
  
 m_fHasDebugInfo  
 0 以外の値 (`TRUE`) 場合は、スタック フレームは無効になっているコードに関連付けられています。  
  
 m_fHasDebugInfo  
 0 以外の値 (`TRUE`) セッション デバッグ マネージャー (SDM) によって、スタック フレームの注釈を付ける場合。  
  
## <a name="remarks"></a>Remarks  
 この構造体に渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)情報を格納するメソッド。 この構造体が一覧に含まれているにも含まれている、 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)インターフェイスをさらへの呼び出しから返される、 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)メソッド。  
  
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

