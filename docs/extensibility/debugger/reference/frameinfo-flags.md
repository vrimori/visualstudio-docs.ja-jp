---
title: "FRAMEINFO_FLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FRAMEINFO_FLAGS
helpviewer_keywords: FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e05d7471df151642f6495907694a0057ef39dfd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
スタック フレーム オブジェクトは取得する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>メンバー  
 FIF_FUNCNAME  
 初期化/を使用して、`m_bstrFuncName`フィールドです。  
  
 FIF_RETURNTYPE  
 初期化/を使用して、`m_bstrReturnType`フィールドです。  
  
 FIF_ARGS  
 初期化/を使用して、`m_bstrArgs`フィールドです。  
  
 FIF_LANGUAGE  
 初期化/を使用して、`m_bstrLanguage`フィールドです。  
  
 FIF_MODULE  
 初期化/を使用して、`m_bstrModule`フィールドです。  
  
 FIF_STACKRANGE  
 初期化/を使用して、`m_addrMin`と`m_addrMax`(スタックの範囲) フィールドです。  
  
 FIF_FRAME  
 初期化/を使用して、`m_pFrame`フィールドです。  
  
 FIF_DEBUGINFO  
 初期化/を使用して、`m_fHasDebugInfo`フィールドです。  
  
 FIF_STALECODE  
 初期化/を使用して、`m_fStaleCode`フィールドです。  
  
 FIF_ANNOTATEDFRAME  
 初期化/を使用して、`m_fAnnotatedFrame`フィールドです。  
  
 FIF_DEBUG_MODULEP  
 初期化/を使用して、`m_pModule`フィールドです。  
  
 FIF_FUNCNAME_FORMAT  
 関数名の書式を設定します。 結果が返される、`m_bstrFunName`フィールドおよびないその他のフィールドに入力されます。  
  
 FIF_FUNCNAME_RETURNTYPE  
 戻り値の型を追加、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_ARGS  
 引数を追加、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_LANGUAGE  
 言語を追加、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_MODULE  
 モジュール名を追加、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_LINES  
 追加する行の数、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_OFFSET  
 追加、`m_bstrFuncName`フィールドの行の先頭からのバイト オフセットに場合`FIF_FUNCNAME_LINES`が指定されています。 場合`FIF_FUNCNAME_LINES`が指定されていないか、行番号が使用できない場合は、追加のオフセット (バイト単位)、関数の先頭からです。  
  
 FIF_FUNCNAME_ARGS_TYPES  
 各関数の引数の型を追加、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_ARGS_NAMES  
 各関数の引数の名前を追加、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_ARGS_VALUES  
 各関数の引数の値を加算、`m_bstrFuncName`フィールドです。  
  
 FIF_FUNCNAME_ARGS_ALL  
 型、名、およびすべての引数の値を追加、`m_bstrFuncName`フィールドです。  
  
 FIF_ARGS_TYPES  
 引数の型が取得され、書式設定します。  
  
 FIF_ARGS_NAMES  
 引数名が取得され、書式設定します。  
  
 FIF_ARGS_VALUES  
 引数の値が取得され、書式設定します。  
  
 FIF_ARGS_ALL  
 取得し、型、名、およびすべての引数の値の書式を設定します。  
  
 FIF_ARGS_NOFORMAT  
 引数がフォーマットされていないことを指定します (たとえば、かっこと右の引数リストを囲むかっこを追加もしない追加の引数間の区切り記号) です。  
  
 FIF_ARGS_NO_FUNC_EVAL  
 引数の値を取得するときに関数 (プロパティ) の評価が使用しないことを指定します。  
  
 FIF_FILTER_NON_USER_CODE  
 デバッグ エンジンは、含まれていないために、非ユーザー コード フレームをフィルター処理します。  
  
 FIF_ARGS_NO_TOSTRING  
 許可しない`ToString()`関数の評価または関数の引数を返すときに書式設定します。  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 フレームの情報は、ホスト プロセスではなく、ホストされているアプリケーション ドメインから取得する必要があります。  
  
## <a name="remarks"></a>コメント  
 これらのフラグに渡される、 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)と[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)メソッドで初期化するフィールドを示す、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造体または構造体。  
  
 これらのフラグはのどのフィールドを示すためにも使用、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造が返されるときに構造体が使用される、有効です。 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)