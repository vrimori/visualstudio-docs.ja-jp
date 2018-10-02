---
title: FIELD_MODIFIERS |Microsoft Docs
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
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 223a1c0ddf66cc7e309792656f4debd4d1221756
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547682"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[FIELD_MODIFIERS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/field-modifiers)します。  
  
フィールドの型の修飾子を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 フィールドがパブリック アクセスを持つことを示します。  
  
 FIELD_MOD_ACCESS_PROTECTED  
 フィールドにアクセスが保護されていることを示します。  
  
 FIELD_MOD_ACCESS_PRIVATE  
 フィールドがプライベート アクセスを持つことを示します。  
  
 FIELD_MOD_NOMODIFIERS  
 フィールドに修飾子がないことを示します。  
  
 FIELD_MOD_STATIC  
 フィールドが静的であることを示します。  
  
 FIELD_MOD_CONSTANT  
 フィールドが定数であることを示します。  
  
 FIELD_MOD_TRANSIENT  
 フィールドが一時的であることを示します。  
  
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
 フィールドが内部クラスであることを示します。  
  
 FIELD_TYPE_OPTIONAL  
 フィールドが省略可能であることを示します。  
  
 FIELD_MOD_BYREF  
 フィールドが参照の引数であることを示します。 これは、専用のメソッドの引数。  
  
 FIELD_MOD_HIDDEN  
 フィールドを非表示または別のコンテキストで表示する必要があることを示しますたとえば、[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]静的ローカル変数。  
  
 FIELD_MOD_MARSHALASOBJECT  
 フィールドを持つオブジェクトで表すことを示す、`IUnknown`インターフェイス。  
  
 FIELD_MOD_SPECIAL_NAME  
 フィールドなど、特別な名前を持つことを示します`.ctor`コンス トラクター ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]のみ)。  
  
 FIELD_MOD_HIDEBYSIG  
 フィールドがあることを示します、`Overloads`キーワードを適用 ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]のみ)。  
  
 FIELD_MOD_WRITEONLY  
 フィールドが書き込み専用であることを示します。 この値が記載されていない`FIELD_MOD_ALL`関数の評価は、このような書き込み専用のフィールドのみを使用します。 ユーザーを明示的に問い合わせる必要があります`FIELD_MOD_WRITEONLY`フィールド。  
  
 FIELD_MOD_ACCESS_MASK  
 フィールドへのアクセスのマスクを示します。  
  
 FIELD_MOD_MASK  
 フィールド修飾子のマスクを示します。  
  
## <a name="remarks"></a>Remarks  
 使用、`dwModifiers`のメンバー、 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)構造体。  
  
 これらの値は渡されることも、 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)メソッドの特定のフィールドをフィルター処理します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)

