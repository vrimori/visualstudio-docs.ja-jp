---
title: FRAMEINFO_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd2273e7ca2769c5dde43d1c29f08989503659f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949124"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
スタック フレーム オブジェクトを取得する情報を指定します。  
  
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
 初期化/使用、`m_bstrFuncName`フィールド。  
  
 FIF_RETURNTYPE  
 初期化/使用、`m_bstrReturnType`フィールド。  
  
 FIF_ARGS  
 初期化/使用、`m_bstrArgs`フィールド。  
  
 FIF_LANGUAGE  
 初期化/使用、`m_bstrLanguage`フィールド。  
  
 FIF_MODULE  
 初期化/使用、`m_bstrModule`フィールド。  
  
 FIF_STACKRANGE  
 初期化/使用、`m_addrMin`と`m_addrMax`(スタックの範囲) フィールド。  
  
 FIF_FRAME  
 初期化/使用、`m_pFrame`フィールド。  
  
 FIF_DEBUGINFO  
 初期化/使用、`m_fHasDebugInfo`フィールド。  
  
 FIF_STALECODE  
 初期化/使用、`m_fStaleCode`フィールド。  
  
 FIF_ANNOTATEDFRAME  
 初期化/使用、`m_fAnnotatedFrame`フィールド。  
  
 FIF_DEBUG_MODULEP  
 初期化/使用、`m_pModule`フィールド。  
  
 FIF_FUNCNAME_FORMAT  
 関数名の書式を設定します。 結果が返されます、`m_bstrFunName`フィールドおよびないその他のフィールドに入力されます。  
  
 FIF_FUNCNAME_RETURNTYPE  
 戻り値の型を追加、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_ARGS  
 引数を追加、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_LANGUAGE  
 言語を追加、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_MODULE  
 モジュール名を追加、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_LINES  
 追加する行の数、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_OFFSET  
 追加、`m_bstrFuncName`フィールドに、行の先頭からのバイト オフセットの場合`FIF_FUNCNAME_LINES`を指定します。 場合`FIF_FUNCNAME_LINES`が指定されていないか、行番号が使用できない場合は、バイト単位のオフセットを関数の開始から追加します。  
  
 FIF_FUNCNAME_ARGS_TYPES  
 各関数の引数の型を追加、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_ARGS_NAMES  
 各関数の引数の名前を追加、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_ARGS_VALUES  
 各関数の引数の値を加算、`m_bstrFuncName`フィールド。  
  
 FIF_FUNCNAME_ARGS_ALL  
 型、名、およびすべての引数の値を追加、`m_bstrFuncName`フィールド。  
  
 FIF_ARGS_TYPES  
 引数の型が取得されて書式設定します。  
  
 FIF_ARGS_NAMES  
 引数名が取得されて書式設定します。  
  
 FIF_ARGS_VALUES  
 引数の値が取得されて書式設定します。  
  
 FIF_ARGS_ALL  
 取得し、型、名、およびすべての引数の値の書式を設定します。  
  
 FIF_ARGS_NOFORMAT  
 引数はフォーマットされないことを指定します (たとえば、引数リストをかっこで囲むの開閉の追加もしない引数間の区切り記号を追加) します。  
  
 FIF_ARGS_NO_FUNC_EVAL  
 引数の値を取得するときに関数 (プロパティ) の評価が使用しないことを指定します。  
  
 FIF_FILTER_NON_USER_CODE  
 デバッグ エンジンでは、含まれていないために、非ユーザー コード フレームをフィルター処理します。  
  
 FIF_ARGS_NO_TOSTRING  
 許可しない`ToString()`関数の評価または関数の引数を返すときに書式設定します。  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 フレームの情報は、ホスト プロセスではなく、ホストされるアプリケーション ドメインから取得する必要があります。  
  
## <a name="remarks"></a>Remarks  
 これらのフラグに渡される、 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)と[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)メソッドで初期化するフィールドを示す、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造体または構造体。  
  
 これらのフラグは、のどのフィールドを示すためにも使用、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造が返されるときに構造体が使用し、無効です。 これらの値は、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)