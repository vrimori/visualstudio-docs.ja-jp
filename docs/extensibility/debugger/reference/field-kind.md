---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "FIELD_KIND 列挙型"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のオブジェクトに含まれるフィールドの種類を指定します。  
  
## 構文  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## メンバー  
 FIELD\_KIND\_TYPE  
 フィールドが型だけであることを示します。  
  
 FIELD\_KIND\_SYMBOL  
 フィールドがシンボル型と名前であるそのほかの情報ことを示します。  
  
 FIELD\_TYPE\_PRIMITIVE  
 フィールドがプリミティブ型であることを示します。  
  
 FIELD\_TYPE\_STRUCT  
 フィールドが構造体であることを示します。  
  
 FIELD\_TYPE\_CLASS  
 フィールドはクラスであることを示します。  
  
 FIELD\_TYPE\_INTERFACE  
 フィールドがインターフェイスであることを示します。  
  
 FIELD\_TYPE\_UNION  
 フィールドが共用体であることを示します。  
  
 FIELD\_TYPE\_ARRAY  
 フィールドが配列型であることを示します。  
  
 FIELD\_TYPE\_METHOD  
 フィールドはメソッドであることを示します。  
  
 FIELD\_TYPE\_BLOCK  
 フィールドはブロックであることを示します。  
  
 FIELD\_TYPE\_POINTER  
 フィールドがポインターであることを示します。  
  
 FIELD\_TYPE\_ENUM  
 フィールドが列挙型であることを示します。  
  
 FIELD\_TYPE\_LABEL  
 フィールド ラベルがであることを示します。  
  
 FIELD\_TYPE\_TYPEDEF  
 フィールドが型定義であることを示します。  
  
 FIELD\_TYPE\_BITFIELD  
 ビット フィールドがであることを示します。  
  
 FIELD\_TYPE\_NAMESPACE  
 フィールドが名前空間であることを示します。  
  
 FIELD\_TYPE\_MODULE  
 フィールドがモジュールであることを示します。  
  
 FIELD\_TYPE\_DYNAMIC  
 フィールドは動的であることを示します。  
  
 FIELD\_TYPE\_PROP  
 フィールド プロパティがであることを示します。  
  
 FIELD\_TYPE\_INNERCLASS  
 フィールドがの内部クラスであることを示します。  
  
 FIELD\_TYPE\_REFERENCE  
 フィールドが参照であることを示します。  
  
 FIELD\_TYPE\_EXTENDED  
 将来使用するために予約されています。  
  
 FIELD\_SYM\_MEMBER  
 フィールドをメンバーであることを示します。  
  
 FIELD\_SYM\_LOCAL  
 フィールドがローカルであることを示します。  
  
 FIELD\_SYM\_PARAMETER  
 フィールドがパラメーターであることを示します。  
  
 FIELD\_SYM\_THIS  
 フィールドに 「」ポインターであることを示します。  
  
 FIELD\_SYM\_GLOBAL  
 フィールドはグローバルであることを示します。  
  
 FIELD\_SYM\_PROP\_GETTER  
 フィールドのプロパティを取得する方法を示します。  
  
 FIELD\_SYM\_PROP\_SETTER  
 フィールドがプロパティを設定することを示します。  
  
 FIELD\_SYM\_EXTENDED  
 将来使用するために予約されています。  
  
 FIELD\_KIND\_MASK  
 フィールドの種類のマスクを示します。  
  
 FIELD\_TYPE\_MASK  
 フィールドの種類のマスクを示します。  
  
 FIELD\_SYM\_MASK  
 シンボル情報のマスクを示します。  
  
## 解説  
 呼び出しから [GetKind](../Topic/IDebugField::GetKind.md) のメソッドに終了しました。  
  
 フィールドの種類に応じて[QueryInterface](/visual-cpp/atl/queryinterface) はインターフェイスの詳細に特定のフォームの [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスで呼び出すことができます。  たとえば[GetKind](../Topic/IDebugField::GetKind.md)`FIELD_TYPE_METHOD` がを返す場合次に I`DebugField` を [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) のインターフェイスを取得するに `QueryInterface` 呼び出すことができます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../Topic/IDebugField::GetKind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)