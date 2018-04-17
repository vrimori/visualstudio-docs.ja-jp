---
title: FIELD_MODIFIERS |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0040795564aa1d1d599a55928b888ec7cfcfd97e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
フィールドの型の修飾子を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>メンバー  
 FIELD_MOD_ACCESS_TYPE  
 フィールドにアクセスできないことを示します。  
  
 FIELD_MOD_ACCESS_PUBLIC  
 フィールドにパブリック アクセスがあることを示します。  
  
 FIELD_MOD_ACCESS_PROTECTED  
 フィールドのアクセスが保護されていることを示します。  
  
 FIELD_MOD_ACCESS_PRIVATE  
 フィールドが、プライベート アクセスを持つことを示します。  
  
 FIELD_MOD_NOMODIFIERS  
 フィールドの修飾子がないことを示します。  
  
 FIELD_MOD_STATIC  
 フィールドが静的であることを示します。  
  
 FIELD_MOD_CONSTANT  
 フィールドは定数であることを示します。  
  
 FIELD_MOD_TRANSIENT  
 フィールドが一時的なものであることを示します。  
  
 FIELD_MOD_VOLATILE  
 フィールドが揮発性であることを示します。  
  
 FIELD_MOD_ABSTRACT  
 フィールドが抽象であることを示します。  
  
 FIELD_MOD_NATIVE  
 フィールドがネイティブであることを示します。  
  
 FIELD_MOD_SYNCHRONIZED  
 フィールドが同期されていることを示します。  
  
 FIELD_MOD_VIRTUAL  
 フィールドが仮想であることを示します。  
  
 FIELD_MOD_INTERFACE  
 フィールドがインターフェイスであることを示します。  
  
 FIELD_MOD_FINAL  
 フィールドが最終的なであることを示します。  
  
 FIELD_MOD_SENTINEL  
 フィールドが sentinel であることを示します。  
  
 FIELD_MOD_INNERCLASS  
 フィールドは、内部クラスであることを示します。  
  
 FIELD_TYPE_OPTIONAL  
 フィールドが省略可能であることを示します。  
  
 FIELD_MOD_BYREF  
 フィールドが参照の引数であることを示します。 これは特にメソッドの引数です。  
  
 FIELD_MOD_HIDDEN  
 フィールドは非表示にするか別のコンテキストで表示されることを示しますたとえば、[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]静的ローカル変数。  
  
 FIELD_MOD_MARSHALASOBJECT  
 フィールドを持つオブジェクトを表すことを示す、`IUnknown`インターフェイスです。  
  
 FIELD_MOD_SPECIAL_NAME  
 フィールドは、たとえばに特別な名前を持つことを示す`.ctor`コンス トラクター ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]のみ)。  
  
 FIELD_MOD_HIDEBYSIG  
 フィールドを持つことを示す、`Overloads`に適用されているキーワード ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]のみ)。  
  
 FIELD_MOD_WRITEONLY  
 フィールドが書き込み専用であることを示します。 この値は含まれていない`FIELD_MOD_ALL`関数の評価のような書き込み専用のフィールドのみ使用することはできます。 ユーザーが明示的に得る`FIELD_MOD_WRITEONLY`フィールドです。  
  
 FIELD_MOD_ACCESS_MASK  
 フィールド アクセスのマスクを示します。  
  
 FIELD_MOD_MASK  
 フィールド修飾子のマスクを示します。  
  
## <a name="remarks"></a>コメント  
 使用、`dwModifiers`のメンバー、 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)構造体。  
  
 これらの値が渡されるも、 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)を特定のフィールドをフィルター処理するメソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)